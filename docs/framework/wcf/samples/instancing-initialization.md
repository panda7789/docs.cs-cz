---
title: Inicializace vytváření instancí
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ee7d470cb80e913707ae6e92039061efde8fcb7f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715793"
---
# <a name="instancing-initialization"></a>Inicializace vytváření instancí
Tato ukázka rozšiřuje ukázku [sdružování](../../../../docs/framework/wcf/samples/pooling.md) definováním rozhraní `IObjectControl`, které přizpůsobuje inicializaci objektu jeho aktivací a deaktivací. Klient vyvolá metody, které vrátí objekt do fondu a nevrátí objekt do fondu.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="extensibility-points"></a>Body rozšiřitelnosti  
 Prvním krokem při vytváření rozšíření Windows Communication Foundation (WCF) je určení bodu rozšiřitelnosti, který se má použít. V rámci WCF pojem *Třída EndpointDispatcher* odkazuje na komponentu za běhu odpovědnou za převod příchozích zpráv do vyvolání metod na službu uživatele a pro převod návratových hodnot z této metody na odchozí zprávu. Služba WCF vytvoří třída EndpointDispatcher pro každý koncový bod.  
  
 Třída EndpointDispatcher nabízí rozsah koncových bodů (pro všechny zprávy přijaté nebo odesílané službou) pomocí třídy <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. Tato třída umožňuje přizpůsobit různé vlastnosti, které řídí chování třída EndpointDispatcher. Tato ukázka se zaměřuje na vlastnost <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, která odkazuje na objekt, který poskytuje instance třídy služby.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 Ve službě WCF vytvoří třída EndpointDispatcher instance třídy služby pomocí zprostředkovatele instance, který implementuje rozhraní <xref:System.ServiceModel.Dispatcher.IInstanceProvider>. Toto rozhraní má pouze dvě metody:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: při doručení zprávy Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> k vytvoření instance třídy služby pro zpracování zprávy. Frekvence volání této metody je určena vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>. Pokud je například vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> nastavena na hodnotu <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, je vytvořena nová instance třídy služby pro zpracování každé zprávy, která dorazí, takže <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je volána při doručení zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: když instance služby dokončí zpracování zprávy, třída EndpointDispatcher volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>. Stejně jako v metodě <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> je frekvence volání této metody určena vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>.  
  
## <a name="the-object-pool"></a>Fond objektů  
 Třída `ObjectPoolInstanceProvider` obsahuje implementaci fondu objektů. Tato třída implementuje rozhraní <xref:System.ServiceModel.Dispatcher.IInstanceProvider> pro interakci s vrstvou modelu služby. Pokud třída EndpointDispatcher volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> namísto vytvoření nové instance, vlastní implementace vyhledá existující objekt ve fondu v paměti. Pokud je k dispozici, je vrácena. V opačném případě `ObjectPoolInstanceProvider` ověří, zda vlastnost `ActiveObjectsCount` (počet objektů vrácených z fondu) dosáhla maximální velikosti fondu. V takovém případě se vytvoří nová instance, která se vrátí volajícímu a `ActiveObjectsCount` se následně zvýší. V opačném případě je požadavek na vytvoření objektu zařazen do fronty po nastavenou dobu. Implementace pro `GetObjectFromThePool` je uvedena v následujícím ukázkovém kódu.  
  
```csharp
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
  
 Vlastní implementace `ReleaseInstance` přidá uvolněnou instanci zpátky do fondu a sníží hodnotu `ActiveObjectsCount`. Třída EndpointDispatcher může volat tyto metody z různých vláken, a proto je vyžadován synchronizovaný přístup k členům na úrovni třídy ve třídě `ObjectPoolInstanceProvider`.  
  
```csharp
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
  
 Metoda `ReleaseInstance` poskytuje inicializační funkci pro *Vyčištění* . Fond běžně udržuje minimální počet objektů za dobu života fondu. Nicméně můžou existovat období nadměrného využití, které vyžaduje vytvoření dalších objektů ve fondu, aby dosáhly maximálního limitu určeného v konfiguraci. Pokud se ale fond stane méně aktivním, může se stát, že nadbytečné objekty budou dodatečně režijní. Proto když `activeObjectsCount` dosáhne nuly, spustí se časovač nečinnosti, který spustí a provede čisticí cyklus.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 Rozšíření vrstvy ServiceModel jsou zapojená pomocí následujícího chování:  
  
- Chování služby: tyto možnosti umožňují přizpůsobení celého modulu runtime služby.  
  
- Chování koncového bodu: tyto možnosti umožňují přizpůsobení konkrétního koncového bodu služby, včetně třída EndpointDispatcher.  
  
- Chování kontraktu: tyto možnosti umožňují přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientRuntime> nebo <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy v klientovi nebo službě.  
  
- Chování operace: tyto možnosti umožňují přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientOperation> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy v klientovi nebo službě.  
  
 Pro účely rozšíření sdružování objektů je možné vytvořit buď chování koncového bodu, nebo chování služby. V tomto příkladu používáme chování služby, které aplikuje sdružování objektů do každého koncového bodu služby. Chování služby se vytváří implementací rozhraní <xref:System.ServiceModel.Description.IServiceBehavior>. Existuje několik způsobů, jak zajistit, aby měl ServiceModel v potaz vlastní chování:  
  
- Použití vlastního atributu.  
  
- Imperativně přidejte do kolekce chování popisu služby.  
  
- Rozšíření konfiguračního souboru.  
  
 Tato ukázka používá vlastní atribut. Když je <xref:System.ServiceModel.ServiceHost> vytvořená, prověřuje atributy používané v definici typu služby a přidá dostupné chování do kolekce chování popisu služby.  
  
 Rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> má tři metody: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Tyto metody jsou volány službou WCF při inicializaci <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> je volána jako první; umožňuje kontrolu nekonzistencí služby. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> se nazývá Next; Tato metoda je vyžadována pouze ve velmi pokročilých scénářích. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> se volá jako poslední a zodpovídá za konfiguraci modulu runtime. Následující parametry jsou předány do <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
- `Description`: Tento parametr poskytuje popis služby pro celou službu. Dá se použít ke kontrole popisných dat o koncových bodech služby, kontraktech, vazbách a dalších datech přidružených k této službě.  
  
- `ServiceHostBase`: Tento parametr poskytuje <xref:System.ServiceModel.ServiceHostBase>, který se právě inicializuje.  
  
 Ve vlastní implementaci <xref:System.ServiceModel.Description.IServiceBehavior> je vytvořena instance nové instance `ObjectPoolInstanceProvider` a přiřazena k vlastnosti <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> v každém <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>, který je připojen k <xref:System.ServiceModel.ServiceHostBase>.  
  
```csharp
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
  
 Kromě <xref:System.ServiceModel.Description.IServiceBehavior> implementace má `ObjectPoolingAttribute` třídy několik členů k přizpůsobení fondu objektů pomocí argumentů atributu. Mezi tyto členy patří `MaxSize`, `MinSize`, `Enabled` a `CreationTimeout`, aby odpovídaly sadě funkcí sdružování objektů poskytované službou .NET Enterprise Services.  
  
 Chování sdružování objektů lze nyní přidat do služby WCF zadáním poznámky k implementaci služby pomocí nově vytvořeného vlastního atributu `ObjectPooling`.  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Zapojování aktivace a deaktivace  
 Hlavním cílem sdružování objektů je optimalizovat krátkodobé objekty s poměrně nákladným vytvořením a inicializací. Proto může aplikace výrazně zvýšit výkon při správném použití. Vzhledem k tomu, že objekt je vrácen z fondu, konstruktor je volán pouze jednou. Některé aplikace však vyžadují určitou úroveň řízení, aby bylo možné inicializovat a vyčistit prostředky používané během jednoho kontextu. Například objekt, který se používá pro sadu výpočtů, může obnovit svá soukromá pole před zpracováním dalšího výpočtu. Podnikové služby povolily tento druh inicializace specifického kontextu tím, že umožňují vývojářům objektů přepsat `Activate` a `Deactivate` metody ze <xref:System.EnterpriseServices.ServicedComponent> základní třídy.  
  
 Fond objektů volá metodu `Activate` těsně před vrácením objektu z fondu. `Deactivate` se volá, když se objekt vrátí zpátky do fondu. Základní třída <xref:System.EnterpriseServices.ServicedComponent> obsahuje také vlastnost `boolean` nazvanou `CanBePooled`, kterou lze použít pro oznamování fondu, zda lze objekt dále vyřadit do fondu.  
  
 Pro napodobení této funkci ukázka deklaruje veřejné rozhraní (`IObjectControl`), které má výše uvedené členy. Toto rozhraní je pak implementováno pomocí tříd služeb určených k poskytnutí inicializace specifického kontextu. Implementaci <xref:System.ServiceModel.Dispatcher.IInstanceProvider> je třeba upravit tak, aby splňovala tyto požadavky. Nyní při každém získání objektu voláním metody `GetInstance` je nutné zkontrolovat, zda objekt implementuje `IObjectControl.` Pokud je, je nutné volat metodu `Activate` odpovídajícím způsobem.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Při vrácení objektu do fondu je před přidáním objektu zpět do fondu vyžadováno ověření vlastnosti `CanBePooled`.  
  
```csharp  
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
  
 Vzhledem k tomu, že se vývojář služby může rozhodnout, zda lze objekt vytvořit do fondu, může počet objektů ve fondu v daném čase přecházet pod minimální velikostí. Proto je nutné ověřit, zda počet objektů předržíte pod minimální úrovní a provést nezbytnou inicializaci v postupu vyčištění.  
  
```csharp  
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
  
 Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
