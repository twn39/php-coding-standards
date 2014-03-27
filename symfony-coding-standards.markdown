Symfony编码规范 
====================
**Symfony** 是一款当前非常流行的基于MVC架构的企业级PHP框架，他定义了自己的一套PHP编码规范，这套规范同样也很适用于普通的用户。


遵循**Symfony**编码规范的示例代码：

```
<?php

/*
 * This file is part of the Symfony package.
 *
 * (c) Fabien Potencier <fabien@symfony.com>
 *
 * For the full copyright and license information, please view the LICENSE
 * file that was distributed with this source code.
 */

namespace Acme;

/**
 * Coding standards demonstration.
 */
class FooBar
{
    const SOME_CONST = 42;

    private $fooBar;

    /**
     * @param string $dummy Some argument description
     */
    public function __construct($dummy)
    {
        $this->fooBar = $this->transformText($dummy);
    }

    /**
     * @param string $dummy Some argument description
     * @param array  $options
     *
     * @return string|null Transformed input
     *
     * @throws \RuntimeException
     */
    private function transformText($dummy, array $options = array())
    {
        $mergedOptions = array_merge(
            array(
                'some_default' => 'values',
                'another_default' => 'more values',
            ),
            $options
        );

        if (true === $dummy) {
            return;
        }
        if ('string' === $dummy) {
            if ('values' === $mergedOptions['some_default']) {
                return substr($dummy, 0, 5);
            }

            return ucwords($dummy);
        }
        throw new \RuntimeException(sprintf('Unrecognized dummy option "%s"', $dummy));
    }
}
```

结构
--------------
* 每个逗号分隔符后面添加一个空格
* 在(==, &&, ...)操作符前后各添加一个空格
* 在多行数组的每个数组元素后添加一个逗号（,），即使是最后一个元素也不例外
* 在return语句前保留一个空行，除非这个return语句单独存在于一个语句块中，例如（if语句）
* Use braces to indicate control structure body regardless of the number of statements it contains
* Define one class per file - this does not apply to private helper classes that are not intended to be instantiated from the outside and thus are not concerned by the PSR-0 standard
* Declare class properties before methods
* Declare public methods first, then protected ones and finally private ones
* Use parentheses when instantiating classes regardless of the number of arguments the constructor has
* Exception message strings should be concatenated using sprintf


命名方式
-----------------

* 对于变量，函数，方法，参数等使用驼峰式命名法，即首字母小写，以后每个单词以首字母大写分割，例如（camelCase）
* 对于可选的参数名使用下划线分割
* 对所有的类（class）使用命名空间（namespace）
* Prefix abstract classes with _Abstract_. Please note some early Symfony2 classes do not follow this convention and have not been renamed for backward compatibility reasons. However all new abstract classes must follow this naming convention;
* Suffix interfaces with _Interface_;
* Suffix traits with _Trait_;
* Suffix exceptions with _Exception_;
* Use alphanumeric characters and underscores for file names;
* Don't forget to look at the more verbose Conventions document for more subjective naming considerations


Service Naming Conventions
-----------------------------

* A service name contains groups, separated by dots;
* The DI alias of the bundle is the first group (e.g. _fos\_user_);
* Use lowercase letters for service and parameter names;
* A group name uses the underscore notation;
* Each service has a corresponding parameter containing the class name, following the **SERVICE NAME.class** convention.


Documentation
----------------------

* Add PHPDoc blocks for all classes, methods, and functions;
* Omit the _@return_ tag if the method does not return anything;
* The **@package** and **@subpackage** annotations are not used.

