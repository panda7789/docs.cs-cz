---
title: Vlastní doba života
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1946608c69401fb08f6eb458a8adabea24563963
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520768"
---
# <a name="custom-lifetime"></a>Vlastní doba života

Tato ukázka předvádí, jak psát rozšíření Windows Communication Foundation (WCF) k poskytování služeb vlastní doba života pro sdílené instance služby WCF.

> [!NOTE]
> Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto článku.

## <a name="shared-instancing"></a>Sdílené vytváření instancí

WCF nabízí několik vytvoření instance režimů pro vaše instance služby. Sdílené vytvoření instance režimu popsaná v tomto článku poskytuje způsob, jak sdílet instanci služby mezi několika kanály. Klienti mohou kontaktovat metoda factory ve službě a vytvořit nový kanál komunikaci. Následující fragment kódu ukazuje, jak klientská aplikace vytvoří nový kanál do existující instance služby:

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

Na rozdíl od ostatních vytvoření instance režimech sdílené vytvoření instance režimu má jedinečný způsob, jak uvolnění instancí služby. Ve výchozím nastavení, když jsou uzavřeny všechny kanály pro <xref:System.ServiceModel.InstanceContext>, modul runtime služby WCF zkontroluje, zda služba <xref:System.ServiceModel.InstanceContextMode> nastaven na <xref:System.ServiceModel.InstanceContextMode.PerCall> nebo <xref:System.ServiceModel.InstanceContextMode.PerSession>a pokud to uvolní instanci a nároky prostředky. Pokud vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> je používán, vyvolá WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda implementace poskytovatele před uvolněním instance. Pokud <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> vrátí `true` se uvolní instanci, jinak <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je zodpovědný za upozornění `Dispatcher` ze stavu nečinnosti pomocí metody zpětného volání. To se provádí pomocí volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metoda zprostředkovatele.

Tato ukázka předvádí, jak můžete zpoždění uvolnění <xref:System.ServiceModel.InstanceContext> s časový limit nečinnosti 20 sekund.

## <a name="extending-the-instancecontext"></a>Rozšíření kontextu InstanceContext

Ve službě WCF <xref:System.ServiceModel.InstanceContext> je propojení mezi instance služby a `Dispatcher`. WCF umožňuje rozšířit tak, že přidáte nový stav a chování pomocí způsobu rozšiřitelném objektu této součásti modulu runtime. Vzor rozšiřitelném objektu se používá ve službě WCF buď rozšířit existující třídy modulu runtime s novými funkcemi nebo přidávání nových funkcí stavu k objektu. Existují tři rozhraní ve vzoru rozšiřitelném objektu: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, a <xref:System.ServiceModel.IExtensionCollection%601>.

<xref:System.ServiceModel.IExtensibleObject%601> Rozhraní implementují objekty umožňující rozšíření, která přizpůsobit jejich funkce.

<xref:System.ServiceModel.IExtension%601> Rozhraní implementují objekty, které může být rozšíření třídy typu `T`.

A nakonec <xref:System.ServiceModel.IExtensionCollection%601> rozhraní je kolekce <xref:System.ServiceModel.IExtension%601> implementace, které umožňuje načítání implementace <xref:System.ServiceModel.IExtension%601> podle jejich typu.

Proto aby bylo možné rozšířit <xref:System.ServiceModel.InstanceContext>, musí implementovat <xref:System.ServiceModel.IExtension%601> rozhraní. V tento ukázkový projekt `CustomLeaseExtension` třída obsahuje tuto implementaci.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601> Rozhraní poskytuje dva způsoby <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A>. Jak naznačují jejich názvy, jsou tyto dvě metody volá, když modul runtime připojí a odpojí rozšíření do instance <xref:System.ServiceModel.InstanceContext> třídy. V této ukázce `Attach` metoda se používá ke sledování <xref:System.ServiceModel.InstanceContext> objekt, který patří k aktuální instanci rozšíření.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Kromě toho musíte přidat nezbytné provádění na rozšíření pro zajištění podpory delší životnost. Proto `ICustomLease` rozhraní je deklarována s požadovanou metody a je implementována v `CustomLeaseExtension` třídy.

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

Když WCF vyvolá <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda ve <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace, toto volání se směruje na <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metodu `CustomLeaseExtension`. Pak, bude `CustomLeaseExtension` zkontroluje jeho privátní stav chcete zobrazit, zda <xref:System.ServiceModel.InstanceContext> nečinnosti. Pokud je nečinné, vrátí `true`. V opačném případě spustí časovač po zadanou dobu životnosti rozšířené.

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

V časovače `Elapsed` událostí, aby bylo možné spustit další cyklus vyčištění je volána funkce zpětného volání dispečerem.

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

Neexistuje žádný způsob, jak obnovit spuštěné časovač při přijme novou zprávu pro instanci, který se přesouvá do nečinného stavu.

Implementuje vzorek <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> zachycení volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda a tras do `CustomLeaseExtension`. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Je součástí implementace `CustomLifetimeLease` třídy. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Je vyvolána metoda WCF se uvolnit instance služby. Existuje však pouze jedna instance konkrétní třídy `ISharedSessionInstance` implementace ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kolekce. To znamená, že neexistuje žádný způsob, že pokud <xref:System.ServiceModel.InstanceContext> je uzavřený v době kontroly WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda. Proto tato ukázka používá vlákno uzamčení k serializaci požadavků <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody.

> [!IMPORTANT]
> Použití uzamčení podprocesu není doporučený postup vzhledem k tomu, že serializace může mít vážný vliv výkon vaší aplikace.

Soukromý člen pole se používá v `CustomLifetimeLease` třídy ke sledování stavu nečinnosti a vrátí <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metody. Pokaždé, když <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoda je volána, `isIdle` pole je vrácena a obnovit `false`.  To je velmi důležité, nastavte hodnotu `false` Pokud chcete mít jistotu dispečer volání <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metody.

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

Pokud <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> vrátí metoda `false`, dispečer zaregistruje funkci zpětného volání pomocí <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> metoda. Tato metoda přijímá odkaz na <xref:System.ServiceModel.InstanceContext> se vydávají. Proto se můžete dotazovat vzorový kód `ICustomLease` zadejte příponu a zkontrolujte `ICustomLease.IsIdle` v rozšířené stavové vlastnosti.

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

Před `ICustomLease.IsIdle` zaškrtnuté vlastnosti, vlastnost zpětného volání je potřeba nastavit, protože to je nezbytné pro `CustomLeaseExtension` dispečer upozornit, když se změní na nečinnosti. Pokud `ICustomLease.IsIdle` vrátí `true`, `isIdle` soukromý člen jednoduše nastavený `CustomLifetimeLease` k `true` a volá metodu zpětného volání. Protože kód drží zámek, ostatní vlákna nelze změnit hodnotu tento privátní člen. A při příštím volání dispečer <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, vrátí `true` a umožňuje uvolnění instance dispečeru.

Teď, když se dokončí připravovat základy pro vlastní rozšíření, musí být připojili k modelu služby. K připojení `CustomLeaseExtension` implementaci <xref:System.ServiceModel.InstanceContext>, poskytuje WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> rozhraní k provedení spuštění z <xref:System.ServiceModel.InstanceContext>. V ukázce `CustomLeaseInitializer` třída implementuje toto rozhraní a přidá instanci `CustomLeaseExtension` k <xref:System.ServiceModel.InstanceContext.Extensions%2A> kolekce z jedinou metodou inicializace. Tato metoda je volána metodou dispečera při inicializaci <xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Nakonec <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementace je připojili k modelu služby s použitím <xref:System.ServiceModel.Description.IServiceBehavior> implementace. Tato implementace se umístí do `CustomLeaseTimeAttribute` třídy a také se odvozuje od `Attribute` základní třída vystavit toto chování jako atribut.

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

Toto chování lze přidat do třídy Ukázka služby s anotací `CustomLeaseTime` atribut.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).

3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
