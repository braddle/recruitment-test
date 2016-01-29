# Espresso Machine Interface

We drink a lot of coffee in the office, we spent 600 pounds on a professional coffee machine, buy the best beans and used
to have a coffee can mountain until we destroyed it playing bowling with the office swivel chairs at a party...

You challenge is to take the interface below and write a class this implements and fully complies to this interface

We have already written a set of unit tests which will be used to test your implementation

 - You MUST NOT change any of the existing methods defined in the interface
 - You should not print or display anything
 - You may add additional methods to your implementation
 - Exceptions are listed in the order they should be thrown
 - The standard WaterContainer contains 2 litres but other sizes can be attached. common sizes are the 10 litre or mains
   water supply
 - The standard BeanContainer holds 50 beans but other sizes can be attached.  a 200  bean container is common.

 ## Code

 ### Beans Container Interface

 ```php
 interface BeansContainer
  {
    /**
     * Adds beans to the container
     *
     * @param integer $numSpoons number of spoons of beans
     * @throws ContainerFullException, EspressoMachineContainerException
     *
     * @return void
     */
    public function addBeans($numSpoons);
    /**
     * Get $numSpoons from the container
     *
     * @throws EspressoMachineContainerException
     * @param integer $numSpoons number of spoons of beans
     * @return integer
     */
    public function useBeans($numSpoons);
    /**
     * Returns the number of spoons of beans left in the container
     *
     * @return integer
     */
    public function getBeans();
  }
 ```

 ### Water Container Interface

 ```php
 interface WaterContainer
  {
    /**
     * Adds water to the coffee machine's water tank
     *
     * @param float $litres
     * @throws ContainerFullException, EspressoMachineContainerException
     *
     * @return void
     */
    public function addWater($litres);
    /**
     * Use $litres from the container
     *
     * @throws EspressoMachineContainerException
     * @param float $litres
     * @return integer
     */
    public function useWater($litres);
    /**
     * Returns the volume of water left in the container
     *
     * @return float number of litres
     */
    public function getWater();
  }
 ```

### Espresso Machine Interface

```php
 /**
  * A single espresso uses 1 spoon of beans and 0.05 litres of water
  * A double espresso uses 2 spoons of beans and 0.10 litres of water
  *
  * The machine MUST be descaled after every 5 litres of Espresso made
  *    Descaling uses 1 litres of water
  *    You CANNOT make coffee while the machine needs descaling
  *    The machine will start with no beans or water in its containers
  *
  */
 interface EspressoMachineInterface extends BeansContainer, WaterContainer
 {
   /**
    * Runs the process to descale the machine
    * so the machine can be used make coffee
    * uses 1 litre of water
    *
    * @throws NoWaterException
    *
    * @return void
    */
   public function descale();
   /**
    * Runs the process for making Espresso
    *
    * @throws DescaleNeededException, NoBeansException, NoWaterException
    *
    * @return float of litres of coffee made
    */
   public function makeEspresso();
   /**
    * @see makeEspresso
    * @throws DescaleNeededException, NoBeansException, NoWaterException
    *
    * @return float of litres of coffee made
    */
   public function makeDoubleEspresso();
   /**
    * This method controls what is displayed on the screen of the machine
    * Returns ONE of the following human readable statuses in the following preference order:
    *
    * Descale needed
    * Add beans and water
    * Add beans
    * Add water
    * {Integer} Espressos left
    *
    * Please note you should return "Add water" if the machine needs descaling and doesn't have enough water
    *
    * @return string
    */
   public function getStatus();
   /**
    * @param BeansContainer $container
    */
   public function setBeansContainer(BeansContainer $container);
   /**
    * @return BeansContainer
    */
   public function getBeansContainer();
   /**
    * @param WaterContainer $container
    */
   public function setWaterContainer(WaterContainer $container);
   /**
    * @return WaterContainer
    */
   public function getWaterContainer();
 }
```

### Exceptions

```php
 class EspressoMachineException extends Exception {}
 class NoWaterException extends EspressoMachineException {}
 class NoBeansException extends EspressoMachineException {}
 class DescaleNeededException extends EspressoMachineException {}
 class EspressoMachineContainerException extends Exception {}
 class ContainerFullException extends EspressoMachineContainerException {}
```







