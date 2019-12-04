---
title: Vlastní doba života
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715469"
---
# <a name="custom-lifetime"></a>Vlastní doba života

Tato ukázka předvádí, jak napsat rozšíření Windows Communication Foundation (WCF), které poskytuje vlastní služby životnosti pro sdílené instance služby WCF.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto článku.

## <a name="shared-instancing"></a>Sdílené vytváření instancí

WCF nabízí několik režimů vytváření instancí pro vaše instance služby. Režim sdíleného vytváření instancí, který je popsaný v tomto článku, poskytuje způsob, jak sdílet instanci služby mezi několika kanály. Klienti můžou ve službě kontaktovat výrobní metodu a vytvořit nový kanál pro zahájení komunikace. Následující fragment kódu ukazuje, jak klientská aplikace vytvoří nový kanál do existující instance služby:

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

Na rozdíl od jiných režimů vytváření instancí má režim sdíleného vytváření instancí jedinečný způsob, jak tyto instance služby uvolnit. Když se ve výchozím nastavení pro <xref:System.ServiceModel.InstanceContext>zavřou všechny kanály, modul runtime služby WCF zkontroluje, jestli je <xref:System.ServiceModel.InstanceContextMode> služby nakonfigurované na <xref:System.ServiceModel.InstanceContextMode.PerCall> nebo <xref:System.ServiceModel.InstanceContextMode.PerSession>, a pokud tak uvolní instanci a vyžádá prostředky. Pokud se používá vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, WCF vyvolá metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> implementace zprostředkovatele před uvolněním instance. Pokud <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> vrátí `true` instance, v opačném případě <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je zodpovědná za oznamování `Dispatcher` stavu nečinnosti pomocí metody zpětného volání. To se provádí voláním metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> zprostředkovatele.

Tato ukázka předvádí, jak můžete zpozdit uvolnění <xref:System.ServiceModel.InstanceContext> s časovým limitem nečinnosti 20 sekund.

## <a name="extending-the-instancecontext"></a>Rozšíření InstanceContext

V rámci WCF je <xref:System.ServiceModel.InstanceContext> propojení mezi instancí služby a `Dispatcher`. Služba WCF umožňuje rozšířit tuto komponentu modulu runtime přidáním nového stavu nebo chování pomocí jeho modelu rozšiřitelného objektu. Model rozšiřitelného objektu se používá ve službě WCF pro rozšiřující existující běhové třídy s novými funkcemi nebo pro přidání nových funkcí stavu do objektu. Existují tři rozhraní ve vzoru rozšiřitelného objektu: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>a <xref:System.ServiceModel.IExtensionCollection%601>.

Rozhraní <xref:System.ServiceModel.IExtensibleObject%601> je implementováno pomocí objektů a umožňuje rozšíření, která přizpůsobují jejich funkce.

Rozhraní <xref:System.ServiceModel.IExtension%601> je implementováno objekty, které mohou být rozšíření třídy typu `T`.

A nakonec <xref:System.ServiceModel.IExtensionCollection%601> rozhraní je kolekce <xref:System.ServiceModel.IExtension%601> implementace, které umožňují načíst implementaci <xref:System.ServiceModel.IExtension%601> podle jejich typu.

Proto pro účely rozšiřování <xref:System.ServiceModel.InstanceContext>musíte implementovat rozhraní <xref:System.ServiceModel.IExtension%601>. V tomto ukázkovém projektu třída `CustomLeaseExtension` obsahuje tuto implementaci.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

Rozhraní <xref:System.ServiceModel.IExtension%601> má dvě metody <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A>. Protože jejich názvy implikují, tyto dvě metody jsou volány, když modul runtime připojí a odpojí rozšíření s instancí třídy <xref:System.ServiceModel.InstanceContext>. V této ukázce je `Attach` metoda použita k udržení přehledu o <xref:System.ServiceModel.InstanceContext> objektu, který patří do aktuální instance rozšíření.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Kromě toho musíte do rozšíření přidat nezbytnou implementaci, která poskytuje rozšířenou podporu životního cyklu. Proto rozhraní `ICustomLease` je deklarováno s požadovanými metodami a je implementováno ve třídě `CustomLeaseExtension`.

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

Když WCF vyvolá metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> v implementaci <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, toto volání je směrováno na metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `CustomLeaseExtension`. Pak `CustomLeaseExtension` zkontroluje svůj privátní stav, aby bylo možné zjistit, zda <xref:System.ServiceModel.InstanceContext> nečinný. Pokud je nečinné, vrátí `true`. V opačném případě spustí časovač pro zadanou dobu rozšířené doby života.

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

V události `Elapsed` časovače je volána funkce zpětného volání v dispečeru, aby bylo možné spustit další čisticí cyklus.

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

Neexistuje žádný způsob, jak obnovit spuštěný časovač při doručení nové zprávy pro instanci, která je přesunuta do stavu nečinnosti.

Ukázka implementuje <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> pro zachycení volání metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> a jejich směrování do `CustomLeaseExtension`. Implementace <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> je obsažena v `CustomLifetimeLease` třídě. Metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> je vyvolána, když se chystá služba WCF vydávat instanci služby. V kolekci <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> ServiceBehavior ale existuje jenom jedna instance konkrétní `ISharedSessionInstance` implementace. To znamená, že neexistuje žádný způsob, jak zjistit, zda je <xref:System.ServiceModel.InstanceContext> uzavřen v době, kdy WCF kontroluje metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>. Proto tato ukázka používá uzamykání vláken k serializaci požadavků na metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.

> [!IMPORTANT]
> Použití uzamykání vlákna není doporučený přístup, protože serializace může mít vážně vliv na výkon aplikace.

Pole privátního člena se používá ve třídě `CustomLifetimeLease` ke sledování stavu nečinnosti a je vráceno metodou <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>. Pokaždé, když je volána metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>, je vráceno pole `isIdle` a resetování na `false`.  Je nutné nastavit tuto hodnotu na `false`, abyste se ujistili, že Dispečer volá metodu <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

Pokud metoda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> vrátí `false`, dispečer zaregistruje funkci zpětného volání pomocí metody <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>. Tato metoda obdrží odkaz na vydanou <xref:System.ServiceModel.InstanceContext>. Proto může vzorový kód zadat dotaz na rozšíření typu `ICustomLease` a kontrolovat vlastnost `ICustomLease.IsIdle` v rozšířeném stavu.

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

Před zaškrtnutím vlastnosti `ICustomLease.IsIdle` je nutné nastavit vlastnost zpětného volání, protože je to nezbytné pro `CustomLeaseExtension`, aby byl dispečer upozorněn, když se změní na nečinný. Pokud `ICustomLease.IsIdle` vrátí `true`, je `isIdle` soukromý člen jednoduše nastaven v `CustomLifetimeLease` na `true` a volá metodu zpětného volání. Vzhledem k tomu, že kód drží zámek, jiné vlákna nemohou změnit hodnotu tohoto privátního člena. A při příštím volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, vrátí `true` a umožňuje dispečerovi uvolnit instanci.

Teď, když je základy pro vlastní rozšíření dokončený, musí být připojený k modelu služby. Chcete-li připojit `CustomLeaseExtension` implementaci do <xref:System.ServiceModel.InstanceContext>, WCF poskytuje rozhraní <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> k provedení zaváděcího programu <xref:System.ServiceModel.InstanceContext>. V ukázce třída `CustomLeaseInitializer` implementuje toto rozhraní a přidá instanci `CustomLeaseExtension` do kolekce <xref:System.ServiceModel.InstanceContext.Extensions%2A> pouze z inicializace metody. Tato metoda je volána dispečerem při inicializaci <xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Nakonec je implementace <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> zapojená do modelu služby pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior>. Tato implementace je umístěna ve třídě `CustomLeaseTimeAttribute` a také je odvozena z <xref:System.Attribute> základní třídy k vystavení tohoto chování jako atributu.

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

Toto chování lze přidat do ukázkové třídy služby tím, že ji přidáte do atributu `CustomLeaseTime`.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
