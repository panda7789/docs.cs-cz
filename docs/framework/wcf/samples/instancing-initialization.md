---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 651029783f4632fc0b404bea8df8bd3790622bfd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388258"
---
# <a name="instancing-initialization"></a>Inicializace vytváření instancí
Tento příklad rozšiřuje [Sdužování](../../../../docs/framework/wcf/samples/pooling.md) ukázka definováním rozhraní, `IObjectControl`, který přizpůsobí inicializace objektu aktivace a deaktivace. Klient volá metody, které vracejí objekt do fondu a objekt, který nesmí vracet do fondu.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="extensibility-points"></a>Body rozšiřitelnosti  
 Prvním krokem při vytváření rozšíření pro Windows Communication Foundation (WCF) je rozhodnout bodu rozšiřitelnosti pro použití. Ve službě WCF termín *EndpointDispatcher* odkazuje na komponentu za běhu pro převod příchozích zpráv do volání metod na uživatele služby a pro převod vrácené hodnoty z této metody na odchozí zprávy . Služba WCF vytvoří EndpointDispatcher pro každý koncový bod.  
  
 Modul nabízí používání rozšíření koncového bodu rozsah (pro všechny zprávy přijatých nebo odeslaných službou) <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> třídy. Tato třída umožňuje přizpůsobit různé vlastnosti ovládacího prvku chování EndpointDispatcher. Tato ukázka se zaměřuje na <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost, která odkazuje na objekt, který poskytuje instance třídy service.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 Ve službě WCF, vytvoří modul instancí třídy služby pomocí instance zprostředkovatele, který implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní. Toto rozhraní má jenom dvě metody:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Při přijetí e-mailu, odesílatel volání <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metodu pro vytvoření instance třídy službu ke zpracování zprávy. Četnost volání této metody se zakládá <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost. Například pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> je nastavena na <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, zpracovat každou zprávu, která dorazí, tak se vytvoří novou instanci třídy služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je volána při každém přijetí e-mailu.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Pokud je instance služby podaří zprávu zpracovat, zavolá modul <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metody. Stejně jako v <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metoda, je určena Četnost volání této metody <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost.  
  
## <a name="the-object-pool"></a>Fond objektů  
 `ObjectPoolInstanceProvider` Třída obsahuje implementaci pro fondu objektů. Tato třída implementuje <xref:System.ServiceModel.Dispatcher.IInstanceProvider> rozhraní pro interakci s vrstva modelu služby. Když volá modul <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> metody, místo vytvoření nové instance, vlastní implementaci hledá existující objekt ve fondu v paměti. Pokud je k dispozici, bude vrácen. V opačném případě `ObjectPoolInstanceProvider` kontroluje, zda `ActiveObjectsCount` vlastností (počet objektů vrácených z fondu) dosáhl maximální velikosti fondu. Pokud ne, novou instanci se vytvoří a vrátit zpět volajícímu a `ActiveObjectsCount` se následně zvýší. Jinak požadavek na vytvoření objektů je zařadí do fronty pro nakonfigurovaného časového období. Implementace `GetObjectFromThePool` je znázorněno v následujícím ukázkovém kódu.  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 Vlastní `ReleaseInstance` implementace přidá vydané instanci zpět do fondu a sníží `ActiveObjectsCount` hodnotu. Modul může tyto metody volat z různých vláken a proto synchronizaci přístupu k členům třídy úrovni v `ObjectPoolInstanceProvider` třída je povinné.  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 `ReleaseInstance` Poskytuje metody *vyčistit inicializace* funkce. Fondu obvykle udržuje minimální počet objektů, které po dobu životnosti fondu. Může však být období nadměrnému využití, které vyžadují vytvoření další objekty ve fondu k dosažení maximální limit zadaný v konfiguraci. Nakonec po fond bude méně aktivní těchto nadbytečné objektů se může stát další režii. Proto když `activeObjectsCount` dosáhne nuly, je spuštěn nečinný časovače, který se aktivuje a provede vyčištění cyklu.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozšíření modelu vrstvy se připojili pomocí následujícího chování:  
  
-   Chování služby: Tyto rutiny umožňují pro přizpůsobení celé služby modulu runtime.  
  
-   Chování koncového bodu: Tyto rutiny umožňují pro přizpůsobení koncového bodu konkrétní služby, včetně EndpointDispatcher.  
  
-   Chování kontraktu: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy u klienta nebo služby v uvedeném pořadí.  
  
-   Operace chování: Tyto rutiny umožňují pro přizpůsobení buď <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy u klienta nebo služby v uvedeném pořadí.  
  
 Pro účely objekt sdružování rozšíření je možné vytvořit chování koncového bodu nebo chování služby. V tomto příkladu používáme chování služby, která se vztahuje objekt sdružování schopnost každý koncový bod služby. Chování služby jsou vytvořeny pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní. Ujistěte se, ServiceModel používající vlastní chování několika způsoby:  
  
-   Pomocí vlastního atributu.  
  
-   Imperativně přidáním do kolekce chování popisu služby.  
  
-   Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když <xref:System.ServiceModel.ServiceHost> je vytvořen, zkontroluje atributy použité v definici služby typu a přidá do kolekce chování popis služby k dispozici chování.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Rozhraní obsahuje tři metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Tyto metody jsou volány aplikací WCF při <xref:System.ServiceModel.ServiceHost> je inicializována. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> je volána. To umožňuje službě zkontroloval za účelem nalezení nekonzistencí. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> je volána vedle; Tato metoda je potřeba jenom velmi pokročilých scénářů. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> je volána poslední a je zodpovědná za konfiguraci modulu runtime. Následující parametry jsou předány do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Tento parametr obsahuje popis služby pro celou službu. To lze použít ke kontrole popis data o koncové body služby, kontrakty, vazby a další data související se službou.  
  
-   `ServiceHostBase`: Tento parametr obsahuje <xref:System.ServiceModel.ServiceHostBase> , který je aktuálně inicializována.  
  
 Ve vlastní <xref:System.ServiceModel.Description.IServiceBehavior> implementace, novou instanci třídy `ObjectPoolInstanceProvider` vytvořena a přiřazená <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnost v každém <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> , který je připojen k <xref:System.ServiceModel.ServiceHostBase>.  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace `ObjectPoolingAttribute` třída má několik členů k přizpůsobení fondu objektů pomocí argumentů atributu. Zahrnout tyto členy `MaxSize`, `MinSize`, `Enabled` a `CreationTimeout`, tak, aby odpovídaly objekt sdružování sadu funkcí poskytovanou služeb .NET Enterprise.  
  
 Objekt sdružování chování lze nyní přidat ke službě WCF anotací implementace služby nově vytvořené vlastním `ObjectPooling` atribut.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Zapojení aktivace a deaktivace  
 Primární cílem sdružování objektů je k optimalizaci krátkodobé objekty s poměrně nákladné vytváření a inicializace. Proto ho nakopnout výrazné výkonu přidělit aplikaci pokud správně použili. Protože je objekt vrácen z fondu, je konstruktor volán pouze jednou. Ale některé aplikace vyžadují určité úrovně ovládacího prvku tak, aby se můžou inicializovat a vyčistit prostředky využívané během jednotlivý kontext. Například objekt se používají pro sadu výpočty můžou resetovat jeho privátní pole před zpracováním další výpočtu. Enterprise Services povolit tento typ inicializace specifickým pro kontext tím, že objekt developer přepsat `Activate` a `Deactivate` metody ze <xref:System.EnterpriseServices.ServicedComponent> základní třídy.  
  
 Volání objektu fondu `Activate` metoda těsně před vrácením objekt z fondu. `Deactivate` je volána, když objekt vrátí zpět do fondu. <xref:System.EnterpriseServices.ServicedComponent> Má také základní třídu `boolean` vlastnost s názvem `CanBePooled`, které je možné oznámit fondu, jestli objekt může dále fondu.  
  
 Tak, aby napodoboval tuto funkci, ukázka deklaruje veřejné rozhraní (`IObjectControl`), který má výše uvedené členy. Toto rozhraní následně implementované třídy určená k zajištění určité Inicializace kontextu služby. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Implementace musí upravit tak, aby tyto požadavky splňují. Nyní pokaždé, když získáte objektu voláním `GetInstance` metodu, musíte zkontrolovat, zda daný objekt implementuje `IObjectControl.` Pokud ano, musíte zavolat `Activate` metoda odpovídajícím způsobem.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Při vrácení objektu do fondu, je třeba použít kontrolu `CanBePooled` vlastnost před přidáním objektu zpět do fondu.  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 Protože vývojářem služeb se můžete rozhodnout, jestli objekt může být ve fondu, můžete počet objektů ve fondu v daném okamžiku přejít menší než minimální velikost. Musíte proto zkontrolujte, zda počet objektů pod minimální úroveň a provést nezbytné inicializace v postupu čištění.  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy Enter v každé okno konzoly pro vypnutí klienta a služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a>Viz také
