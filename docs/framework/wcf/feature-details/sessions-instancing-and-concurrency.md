---
title: Relace, vytváření instancí a souběžnost
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 19dedddadad2f27acdeeaceb2c186a731fa79c32
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243112"
---
# <a name="sessions-instancing-and-concurrency"></a>Relace, vytváření instancí a souběžnost
*Relace* je korelace všech zpráv odeslaných mezi dvěma koncovými body. *Instance* označuje řízení životnosti uživatelem definovaných objektů služby a jejich souvisejících <xref:System.ServiceModel.InstanceContext> objektů. *Souběžnost* je termín daný řízení počtu podprocesů provádějících <xref:System.ServiceModel.InstanceContext> ve stejnou dobu.  
  
 Toto téma popisuje tato nastavení, jak je používat a různé interakce mezi nimi.  
  
## <a name="sessions"></a>Relace  
 Pokud smlouva o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> poskytování <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>služeb nastaví vlastnost , tato smlouva říká, že všechna volání (to znamená, že základní zprávy výměny, které podporují volání) musí být součástí stejné konverzace. Pokud smlouva určuje, že umožňuje relace, ale nevyžaduje ji, klienti se mohou připojit a buď vytvořit relaci, nebo ne. Pokud relace skončí a zpráva je odeslána prostředpo stejné relace založené kanálu je vyvolána výjimka.  
  
 Relace WCF mají následující hlavní koncepční funkce:  
  
- Jsou explicitně iniciovány a ukončeny volající aplikací.  
  
- Zprávy doručené během relace jsou zpracovány v pořadí, ve kterém jsou přijímány.  
  
- Relace korelují skupinu zpráv do konverzace. Význam této korelace je abstrakce. Jeden kanál založený na relaci může například korelovat zprávy založené na sdíleném síťovém připojení, zatímco jiný kanál založený na relaci může korelovat zprávy na základě sdílené značky v textu zprávy. Funkce, které lze odvodit z relace závisí na povaze korelace.  
  
- Neexistuje žádné obecné úložiště dat přidružené k relaci WCF.  
  
 Pokud jste obeznámeni <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> s třídou v ASP.NET aplikacích a funkce, které poskytuje, můžete si všimnout následující rozdíly mezi tento druh relace a WCF relací:  
  
- ASP.NET relací jsou vždy inicializovány serverem.  
  
- ASP.NET relace jsou implicitně neuspořádané.  
  
- ASP.NET relace poskytují obecný mechanismus ukládání dat napříč požadavky.  
  
 Klientské aplikace a aplikace služeb interagují s relacemi různými způsoby. Klientské aplikace iniciují relace a pak přijímají a zpracovávají zprávy odeslané v rámci relace. Aplikace služby můžete použít relace jako bod rozšiřitelnosti přidat další chování. To se provádí přímo <xref:System.ServiceModel.InstanceContext> u poskytovatele kontextu vlastní instance.  
  
## <a name="instancing"></a>Vytváření instancí  
 Instancing chování (nastavit pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnosti) <xref:System.ServiceModel.InstanceContext> určuje, jak je vytvořen v reakci na příchozí zprávy. Ve výchozím <xref:System.ServiceModel.InstanceContext> nastavení je každý z nich přidružen k jednomu uživatelem <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> definovanému objektu služby, takže (ve výchozím případě) nastavení vlastnosti také řídí instance uživatelem definovaných objektů služby. Výčet <xref:System.ServiceModel.InstanceContextMode> definuje instance režimy.  
  
 K dispozici jsou následující instance:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Pro <xref:System.ServiceModel.InstanceContext> každý požadavek klienta je vytvořen nový (a proto objekt služby).  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Pro <xref:System.ServiceModel.InstanceContext> každou novou relaci klienta je vytvořen nový (a proto objekt služby) a udržován po dobu životnosti této relace (to vyžaduje vazbu, která podporuje relace).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Jeden <xref:System.ServiceModel.InstanceContext> (a proto objekt služby) zpracovává všechny požadavky klienta po dobu životnosti aplikace.  
  
 Následující příklad kódu ukazuje <xref:System.ServiceModel.InstanceContextMode> výchozí <xref:System.ServiceModel.InstanceContextMode.PerSession> hodnotu, která je explicitně nastavena na třídě služby.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 A zatímco <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, <xref:System.ServiceModel.InstanceContext> jak často <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> je uvolněna, a vlastnosti řídit, kdy je uvolněn objekt služby.  
  
### <a name="well-known-singleton-services"></a>Známé singleton služby  
 Jedna varianta na objekty služby jedné instance je někdy užitečná: můžete vytvořit objekt služby sami a vytvořit hostitele služby pomocí tohoto objektu. Chcete-li tak učinit, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> musíte <xref:System.ServiceModel.InstanceContextMode.Single> také nastavit vlastnost nebo je vyvolána výjimka při otevření hostitele služby.  
  
 Pomocí <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> konstruktoru vytvořit takovou službu. Poskytuje alternativu k implementaci <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> vlastní, pokud chcete poskytnout konkrétní instance objektu pro použití službou singleton. Toto přetížení můžete použít, když je obtížné vytvořit typ implementace služby (například pokud neimplementuje public konstruktor bez parametrů).  
  
 Všimněte si, že když je objekt k dispozici tohoto konstruktoru, některé funkce související s Windows Communication Foundation (WCF) instance chování pracovat jinak. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, když je k dispozici instance objektu singleton. Podobně je ignorována jakákoli jiná instance release mechanism. Vždy <xref:System.ServiceModel.ServiceHost> se chová, jako <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> by vlastnost <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> je nastavena na pro všechny operace.  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení objektů InstanceContext  
 Můžete také určit, který kanál nebo volání <xref:System.ServiceModel.InstanceContext> relace je přidruženo k jakému objektu, provedením tohoto přidružení sami.  
  
## <a name="concurrency"></a>Souběžnost  
 Souběžnost je řízení počtu podprocesů aktivních <xref:System.ServiceModel.InstanceContext> v jednom okamžiku. To je řízenpomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> s <xref:System.ServiceModel.ConcurrencyMode> výčtu.  
  
 K dispozici jsou následující tři režimy souběžnosti:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Každý kontext instance může mít maximálně jeden podproces zpracování zpráv v kontextu instance najednou. Ostatní vlákna, která chtějí použít stejný kontext instance, musí blokovat, dokud původní vlákno neukončí kontext instance.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Každá instance služby může mít více vláken zpracování zpráv současně. Implementace služby musí být bezpečné pro přístup z více vláken, aby bylo možné použít tento režim souběžnosti.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Každá instance služby zpracovává jednu zprávu najednou, ale přijímá volání operace opětovného účastníka. Služba přijímá pouze tato volání, pokud volá prostřednictvím objektu klienta WCF.  
  
> [!NOTE]
> Pochopení a vývoj kódu, který bezpečně používá více než jedno vlákno může být obtížné úspěšně psát. Před <xref:System.ServiceModel.ConcurrencyMode.Multiple> použitím <xref:System.ServiceModel.ConcurrencyMode.Reentrant> nebo hodnotami se ujistěte, že je služba pro tyto režimy správně navržena. Další informace naleznete v tématu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Použití souběžnosti souvisí s instance režimu. V <xref:System.ServiceModel.InstanceContextMode.PerCall> instance není souběžnost relevantní, protože každá zpráva je <xref:System.ServiceModel.InstanceContext> zpracována novým, a proto nikdy není <xref:System.ServiceModel.InstanceContext>v rozhraní .  
  
 Následující příklad kódu ukazuje <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> nastavení <xref:System.ServiceModel.ConcurrencyMode.Multiple>vlastnosti na .  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Interakce relací s nastavením instancekontextu  
 Relace <xref:System.ServiceModel.InstanceContext> a interakci v závislosti na <xref:System.ServiceModel.SessionMode> kombinaci hodnoty výčtu <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> ve smlouvě a vlastnost na implementaci služby, která řídí přidružení mezi kanály a konkrétní objekty služby.  
  
 V následující tabulce je uveden výsledek příchozího kanálu, který podporuje relace nebo nepodporuje relace <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> dané kombinace <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> hodnot vlastnosti a vlastnosti službou.  
  
|Hodnota InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Percall|- Chování s sessionful kanál: relace a <xref:System.ServiceModel.InstanceContext> pro každý hovor.<br />- Chování s kanálem bez relace: Je vyvolána výjimka.|- Chování s sessionful kanál: relace a <xref:System.ServiceModel.InstanceContext> pro každý hovor.<br />- Chování s kanálem <xref:System.ServiceModel.InstanceContext> bez relace: A pro každý hovor.|- Chování s sessionful kanál: Je vyvolána výjimka.<br />- Chování s kanálem <xref:System.ServiceModel.InstanceContext> bez relace: A pro každý hovor.|  
|PerSession|- Chování s sessionful kanál: Relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />- Chování s kanálem bez relace: Je vyvolána výjimka.|- Chování s sessionful kanál: Relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />- Chování s kanálem <xref:System.ServiceModel.InstanceContext> bez relace: A pro každý hovor.|- Chování s sessionful kanál: Je vyvolána výjimka.<br />- Chování s kanálem <xref:System.ServiceModel.InstanceContext> bez relace: A pro každý hovor.|  
|Single|- Chování s sessionful kanál: <xref:System.ServiceModel.InstanceContext> relace a jeden pro všechny hovory.<br />- Chování s kanálem bez relace: Je vyvolána výjimka.|- Chování s sessionful kanál: relace a <xref:System.ServiceModel.InstanceContext> pro vytvořené nebo uživatelem zadané singleton.<br />- Chování s kanálem <xref:System.ServiceModel.InstanceContext> bez relace: A pro vytvořený nebo uživatelem určený singleton.|- Chování s sessionful kanál: Je vyvolána výjimka.<br />- Chování s kanálem <xref:System.ServiceModel.InstanceContext> bez relace: A pro každý vytvořený singleton nebo pro uživatelem určený singleton.|  
  
## <a name="see-also"></a>Viz také

- [Použití relací](../../../../docs/framework/wcf/using-sessions.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Postupy: Řízení vytváření instancí služby](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Souběžnost](../../../../docs/framework/wcf/samples/concurrency.md)
- [Vytváření instancí](../../../../docs/framework/wcf/samples/instancing.md)
- [Relace](../../../../docs/framework/wcf/samples/session.md)
