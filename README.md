![build](https://github.com/konveyer-framework/dependency-injection/workflows/build/badge.svg)
# The dependency injection container

### This package makes it possible to quickly connect the DI-container to your project.

The container can be used both in automatic mode, using type hints in class constructors, and accept fine-tuning using providers.


**Example automatically make instance**

```
use Konveyer\DependencyInjection\ContainerBuilder;
use YourClass;

$container = ContainerBuilder::build();

$yourClassObject = $container->make(YouClass::class);

```

**Make instance with provider**

```

class YourClass
{
    private MyClassInterface $myImplements;
    
    public function __construct(MyClassInterface $myImplements)
    {
        $this->myImplements = $myImplements;
    }
}

```

```
use Konveyer\DependencyInjection\Provider\Provider

class ClassProvider extends Provider
{
    public function bind(): array
    {
        return [
            MyClassInterface::class => MyImplemensClass::class,
        ];
    }
}

```

```

$yourClassObject = $container->make(YouClass::class, ClassProvider::class);

```
or

```

$container->setProviders(
    YouClass::class => ClassProvider::class,
);

$yourClassObject = $container->make(YouClass::class);

