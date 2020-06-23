---
title: Relace, vytváření instancí a souběžnost
description: Přečtěte si o relacích, vytváření instancí a souběžnosti, způsobu jejich použití a interakcích mezi nimi v WFC.
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 41eef5a962c702eebd6b9a34607b542ec6bbd97b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246542"
---
# <a name="sessions-instancing-and-concurrency"></a>Relace, vytváření instancí a souběžnost
*Relace* je korelace všech zpráv posílaných mezi dvěma koncovými body. Vytváření *instancí* odkazuje na řízení životnosti uživatelem definovaných objektů služeb a jejich souvisejících <xref:System.ServiceModel.InstanceContext> objektů. *Concurrency* je termín uvedený pro řízení počtu vláken spuštěných ve <xref:System.ServiceModel.InstanceContext> stejnou dobu.  
  
 Toto téma popisuje tato nastavení, způsob jejich použití a různé interakce mezi nimi.  
  
## <a name="sessions"></a>Relace  
 Pokud kontrakt služby nastaví <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost na hodnotu <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> , znamená to, že všechna volání (tj. základní výměny zpráv podporující volání) musí být součástí stejné konverzace. Pokud kontrakt určí, že umožňuje relace, ale nevyžaduje jednu, klienti se můžou připojit a navázat relaci nebo ne. V případě ukončení relace a odeslání zprávy přes stejný kanál založený na relaci je vyvolána výjimka.  
  
 Relace WCF mají následující hlavní koncepční funkce:  
  
- Jsou explicitně iniciovány a ukončeny volající aplikací.  
  
- Zprávy dodávané během relace jsou zpracovávány v pořadí, ve kterém byly přijaty.  
  
- Relace korelují skupinu zpráv do konverzace. Význam této korelace je abstrakce. Jeden kanál založený na relaci může například korelovat zprávy na základě sdíleného síťového připojení, zatímco jiný kanál založený na relaci může korelovat zprávy na základě sdílené značky v těle zprávy. Funkce, které mohou být odvozeny z relace závisí na povaze korelace.  
  
- K relaci WCF není přidruženo žádné obecné úložiště dat.  
  
 Pokud znáte <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> třídu v aplikacích ASP.NET a funkcích, které poskytuje, můžete si všimnout následujících rozdílů mezi tímto druhem relace a relacemi WCF:  
  
- ASP.NET relace jsou vždy iniciovány serverem.  
  
- ASP.NET relace jsou implicitně neuspořádané.  
  
- ASP.NET relace poskytují obecný mechanismus pro ukládání dat napříč požadavky.  
  
 Klientské aplikace a aplikace služeb komunikují s relacemi různými způsoby. Klientské aplikace zahajují relace a následně přijímají a zpracovávají zprávy odeslané v rámci relace. Aplikace služby můžou používat relace jako bod rozšíření k přidání dalšího chování. K tomu je potřeba pracovat přímo s <xref:System.ServiceModel.InstanceContext> nebo implementací vlastního poskytovatele kontextu instance.  
  
## <a name="instancing"></a>Vytváření instancí  
 Chování vytváření instancí (nastaveno pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> Vlastnosti) řídí, jak <xref:System.ServiceModel.InstanceContext> je vytvořena v reakci na příchozí zprávy. Ve výchozím nastavení je každá z nich <xref:System.ServiceModel.InstanceContext> přidružena k jednomu uživatelsky definovanému objektu služby, takže (ve výchozím případě) nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnosti také řídí vytváření instancí objektů služeb definovaných uživatelem. <xref:System.ServiceModel.InstanceContextMode>Výčet definuje režimy vytváření instancí.  
  
 K dispozici jsou následující režimy vytváření instancí:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: <xref:System.ServiceModel.InstanceContext> Pro každou žádost klienta se vytvoří nový objekt služby (a tudíž objekt služby).  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Vytvoří se nový <xref:System.ServiceModel.InstanceContext> (a proto objekt služby) pro každou novou relaci klienta a udržuje se po dobu života této relace (vyžaduje vazbu, která podporuje relace).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Jeden <xref:System.ServiceModel.InstanceContext> (a proto objekt služby) zpracovává všechny požadavky klientů po dobu života aplikace.  
  
 Následující příklad kódu ukazuje výchozí <xref:System.ServiceModel.InstanceContextMode> hodnotu, která je <xref:System.ServiceModel.InstanceContextMode.PerSession> explicitně nastavena pro třídu služby.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 A zatímco <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, jak často <xref:System.ServiceModel.InstanceContext> je uvolněna, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> ovládací prvek vlastnosti, když je objekt služby uvolněn.  
  
### <a name="well-known-singleton-services"></a>Dobře známé služby s jedním prvkem  
 Jedna variace objektů služby s jednou instancí je někdy užitečná: objekt služby můžete vytvořit sami a vytvořit hostitele služby pomocí tohoto objektu. K tomu je nutné také nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.InstanceContextMode.Single> nebo při otevření hostitele služby vyvolat výjimku.  
  
 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29>K vytvoření takové služby použijte konstruktor. Poskytuje alternativu k implementaci vlastního objektu, <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> Pokud chcete zadat konkrétní instanci objektu pro použití ve službě typu singleton. Toto přetížení můžete použít, pokud je obtížné sestavit typ implementace služby (například pokud neimplementuje veřejný konstruktor bez parametrů).  
  
 Všimněte si, že když je objekt poskytnut tomuto konstruktoru, některé funkce související s chováním vytváření instancí služby Windows Communication Foundation (WCF) fungují jinak. Volání například <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je poskytnuta instance objektu singleton. Podobně platí, že všechny ostatní mechanismy vydání instance se ignorují. <xref:System.ServiceModel.ServiceHost>Vždy se chová, jako by <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> vlastnost byla nastavena na hodnotu <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení objektů InstanceContext  
 Můžete také řídit, který relační kanál nebo volání jsou přidruženy k <xref:System.ServiceModel.InstanceContext> objektu, který provádí přidružení sami.  
  
## <a name="concurrency"></a>Souběžnost  
 Souběžnost je ovládací prvek počtu aktivních vláken v <xref:System.ServiceModel.InstanceContext> jednom okamžiku. To se řídí pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> s <xref:System.ServiceModel.ConcurrencyMode> výčtem.  
  
 K dispozici jsou následující tři režimy souběžnosti:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Každý kontext instance může mít nejvýše jednu zprávu zpracovávající vlákna v kontextu instance v daném okamžiku. Jiná vlákna, která chtějí použít stejný kontext instance, musí blokovat, dokud původní vlákno neukončí kontext instance.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Každá instance služby může mít souběžně zpracovávané zprávy s více vlákny. Aby bylo možné používat tento režim souběžnosti, musí být implementace služby bezpečná pro přístup z více vláken.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Každá instance služby zpracovává jednu zprávu po druhém, ale přijímá volání operace znovu. Služba akceptuje tato volání pouze při volání prostřednictvím objektu klienta WCF.  
  
> [!NOTE]
> Porozumění a vývoj kódu, který bezpečně používá více než jedno vlákno, může být obtížné zapsat do úspěšného zápisu. Než použijete <xref:System.ServiceModel.ConcurrencyMode.Multiple> <xref:System.ServiceModel.ConcurrencyMode.Reentrant> hodnoty nebo, zajistěte, aby byla služba pro tyto režimy správně navržená. Další informace naleznete v tématu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Použití souběžnosti souvisí s režimem vytváření instancí. V <xref:System.ServiceModel.InstanceContextMode.PerCall> rámci vytváření instancí není souběžnost relevantní vzhledem k tomu, že každá zpráva je zpracována novou <xref:System.ServiceModel.InstanceContext> a proto nikdy není více než jedno vlákno aktivní v <xref:System.ServiceModel.InstanceContext> .  
  
 Následující příklad kódu ukazuje nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> vlastnosti na <xref:System.ServiceModel.ConcurrencyMode.Multiple> .  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace pracují s nastavením InstanceContext  
 Relace a <xref:System.ServiceModel.InstanceContext> interakce v závislosti na kombinaci hodnoty <xref:System.ServiceModel.SessionMode> výčtu ve smlouvě a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnosti pro implementaci služby, která řídí přidružení mezi kanály a konkrétními objekty služby.  
  
 V následující tabulce je uveden výsledek příchozího kanálu buď podporujícího relace, nebo nepodporující relace s ohledem na kombinaci hodnot vlastnosti a vlastnosti příslušné služby <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> .  
  
|Hodnota InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />– Chování s kanálem bez relace: je vyvolána výjimka.|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|-Chování s kanálem relace: je vyvolána výjimka.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|  
|PerSession|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />– Chování s kanálem bez relace: je vyvolána výjimka.|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|-Chování s kanálem relace: je vyvolána výjimka.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|  
|Jeden|– Chování s relačním kanálem: relace a jedna <xref:System.ServiceModel.InstanceContext> pro všechna volání.<br />– Chování s kanálem bez relace: je vyvolána výjimka.|– Chování s kanálem relace: relace a <xref:System.ServiceModel.InstanceContext> pro vytvořeného nebo uživatelem zadaného typu singleton.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro vytvořeného nebo uživatelem zadaného typu singleton.|-Chování s kanálem relace: je vyvolána výjimka.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každý vytvořený typ singleton nebo pro uživatelem zadaný typ singleton.|  
  
## <a name="see-also"></a>Viz také

- [Použití relací](../using-sessions.md)
- [Postupy: Vytvoření služby vyžadující relace](how-to-create-a-service-that-requires-sessions.md)
- [Postupy: Řízení vytváření instancí služby](how-to-control-service-instancing.md)
- [Souběžnost](../samples/concurrency.md)
- [Vytváření instancí](../samples/instancing.md)
- [Relace](../samples/session.md)
