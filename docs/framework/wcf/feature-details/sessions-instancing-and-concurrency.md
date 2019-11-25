---
title: Relace, vytváření instancí a souběžnost
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: b8c0b40ca67de92f4f1b481298a8a26d96e887d4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976080"
---
# <a name="sessions-instancing-and-concurrency"></a>Relace, vytváření instancí a souběžnost
*Relace* je korelace všech zpráv posílaných mezi dvěma koncovými body. Vytváření *instancí* odkazuje na řízení životnosti uživatelem definovaných objektů služeb a jejich souvisejících <xref:System.ServiceModel.InstanceContext>ch objektů. *Concurrency* je termín uvedený pro řízení počtu vláken spouštěných v <xref:System.ServiceModel.InstanceContext> ve stejnou dobu.  
  
 Toto téma popisuje tato nastavení, způsob jejich použití a různé interakce mezi nimi.  
  
## <a name="sessions"></a>Relace  
 Když kontrakt služby nastaví vlastnost <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, znamená to, že všechna volání (tj. základní výměny zpráv podporující volání) musí být součástí stejné konverzace. Pokud kontrakt určí, že umožňuje relace, ale nevyžaduje jednu, klienti se můžou připojit a navázat relaci nebo ne. V případě ukončení relace a odeslání zprávy přes stejný kanál založený na relaci je vyvolána výjimka.  
  
 Relace WCF mají následující hlavní koncepční funkce:  
  
- Jsou explicitně iniciovány a ukončeny volající aplikací.  
  
- Zprávy dodávané během relace jsou zpracovávány v pořadí, ve kterém byly přijaty.  
  
- Relace korelují skupinu zpráv do konverzace. Význam této korelace je abstrakce. Jeden kanál založený na relaci může například korelovat zprávy na základě sdíleného síťového připojení, zatímco jiný kanál založený na relaci může korelovat zprávy na základě sdílené značky v těle zprávy. Funkce, které mohou být odvozeny z relace závisí na povaze korelace.  
  
- K relaci WCF není přidruženo žádné obecné úložiště dat.  
  
 Pokud znáte třídu <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> v aplikacích ASP.NET a funkcích, které poskytuje, můžete si všimnout následujících rozdílů mezi tímto druhem relace a relacemi WCF:  
  
- ASP.NET relace jsou vždy iniciovány serverem.  
  
- ASP.NET relace jsou implicitně neuspořádané.  
  
- ASP.NET relace poskytují obecný mechanismus pro ukládání dat napříč požadavky.  
  
 Klientské aplikace a aplikace služeb komunikují s relacemi různými způsoby. Klientské aplikace zahajují relace a následně přijímají a zpracovávají zprávy odeslané v rámci relace. Aplikace služby můžou používat relace jako bod rozšíření k přidání dalšího chování. K tomu je potřeba pracovat přímo s <xref:System.ServiceModel.InstanceContext> nebo implementací vlastního zprostředkovatele kontextu instance.  
  
## <a name="instancing"></a>Vytváření instancí  
 Chování vytváření instancí (nastavené pomocí vlastnosti <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>) řídí způsob, jakým se vytvoří <xref:System.ServiceModel.InstanceContext> v reakci na příchozí zprávy. Ve výchozím nastavení je každá <xref:System.ServiceModel.InstanceContext> přidružena k jednomu uživatelsky definovanému objektu služby, takže (ve výchozím případě) nastavení vlastnosti <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> také řídí vytváření instancí objektů služeb definovaných uživatelem. Výčet <xref:System.ServiceModel.InstanceContextMode> definuje režimy vytváření instancí.  
  
 K dispozici jsou následující režimy vytváření instancí:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: pro každou žádost klienta se vytvoří nový <xref:System.ServiceModel.InstanceContext> (a proto objekt služby).  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: vytvoří se nový <xref:System.ServiceModel.InstanceContext> (a proto objekt služby) pro každou novou relaci klienta a udržuje se po dobu života této relace (vyžaduje vazbu, která podporuje relace).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: jediný <xref:System.ServiceModel.InstanceContext> (a proto objekt služby) zpracovává všechny žádosti klientů po dobu života aplikace.  
  
 Následující příklad kódu ukazuje výchozí hodnotu <xref:System.ServiceModel.InstanceContextMode>, <xref:System.ServiceModel.InstanceContextMode.PerSession> explicitně nastavené pro třídu služby.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 A zatímco vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> určuje, jak často se <xref:System.ServiceModel.InstanceContext> uvolní, ovládací prvek vlastnosti <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> při uvolnění objektu služby.  
  
### <a name="well-known-singleton-services"></a>Dobře známé služby s jedním prvkem  
 Jedna variace objektů služby s jednou instancí je někdy užitečná: objekt služby můžete vytvořit sami a vytvořit hostitele služby pomocí tohoto objektu. K tomu je nutné také nastavit vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.InstanceContextMode.Single> nebo je vyvolána výjimka při otevření hostitele služby.  
  
 K vytvoření takové služby použijte konstruktor <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType>. Poskytuje alternativu k implementaci vlastního <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType>, pokud chcete poskytnout konkrétní instanci objektu pro použití ve službě typu singleton. Toto přetížení můžete použít, pokud je obtížné sestavit typ implementace služby (například pokud neimplementuje veřejný konstruktor bez parametrů).  
  
 Všimněte si, že když je objekt poskytnut tomuto konstruktoru, některé funkce související s chováním vytváření instancí služby Windows Communication Foundation (WCF) fungují jinak. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je poskytnuta instance objektu singleton. Podobně platí, že všechny ostatní mechanismy vydání instance se ignorují. <xref:System.ServiceModel.ServiceHost> se vždy chová, jako by vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> byla nastavena na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení objektů InstanceContext  
 Můžete také určit, ke kterému kanálu nebo volání relace je přidruženo, které <xref:System.ServiceModel.InstanceContext> objekt provádí přidružení sami.  
  
## <a name="concurrency"></a>Souběžnost  
 Souběžnost je ovládací prvek počtu vláken, která jsou v <xref:System.ServiceModel.InstanceContext> aktivní v jednom okamžiku. To je řízeno pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> s výčtem <xref:System.ServiceModel.ConcurrencyMode>.  
  
 K dispozici jsou následující tři režimy souběžnosti:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: každý kontext instance může mít v daném okamžiku maximálně jedno zprávy zpracovávající vlákno v kontextu instance. Jiná vlákna, která chtějí použít stejný kontext instance, musí blokovat, dokud původní vlákno neukončí kontext instance.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: každá instance služby může mít souběžně zpracovávané zprávy s více vlákny. Aby bylo možné používat tento režim souběžnosti, musí být implementace služby bezpečná pro přístup z více vláken.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: každá instance služby zpracovává jednu zprávu po druhém, ale přijímá volání operace znovu. Služba akceptuje tato volání pouze při volání prostřednictvím objektu klienta WCF.  
  
> [!NOTE]
> Porozumění a vývoj kódu, který bezpečně používá více než jedno vlákno, může být obtížné zapsat do úspěšného zápisu. Před použitím hodnot <xref:System.ServiceModel.ConcurrencyMode.Multiple> nebo <xref:System.ServiceModel.ConcurrencyMode.Reentrant> zajistěte, aby byla služba pro tyto režimy správně navržená. Další informace najdete v tématu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Použití souběžnosti souvisí s režimem vytváření instancí. V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí není souběžnost relevantní, protože každá zpráva je zpracována novým <xref:System.ServiceModel.InstanceContext> a proto nikdy není v <xref:System.ServiceModel.InstanceContext>aktivní více než jedno vlákno.  
  
 Následující příklad kódu ukazuje nastavení vlastnosti <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> na hodnotu <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace pracují s nastavením InstanceContext  
 Relace a <xref:System.ServiceModel.InstanceContext> vzájemně spolupracují v závislosti na kombinaci hodnoty výčtu <xref:System.ServiceModel.SessionMode> ve smlouvě a vlastnosti <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> u implementace služby, která řídí přidružení mezi kanály a konkrétními objekty služby.  
  
 V následující tabulce je uveden výsledek příchozího kanálu buď podporujícího relace, nebo nepodporující relace s předanou kombinací hodnot vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastností služby.  
  
|Hodnota InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />– Chování s kanálem bez relace: je vyvolána výjimka.|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|-Chování s kanálem relace: je vyvolána výjimka.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|  
|PerSession|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />– Chování s kanálem bez relace: je vyvolána výjimka.|– Chování s relačním kanálem: relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|-Chování s kanálem relace: je vyvolána výjimka.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každé volání.|  
|Single|– Chování s relačním kanálem: relace a jedna <xref:System.ServiceModel.InstanceContext> pro všechna volání.<br />– Chování s kanálem bez relace: je vyvolána výjimka.|– Chování s kanálem relace: relace a <xref:System.ServiceModel.InstanceContext> vytvořeného nebo uživatelem zadaného typu singleton.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro vytvořený nebo uživatelem určený typ singleton.|-Chování s kanálem relace: je vyvolána výjimka.<br />– Chování s kanálem bez relace: <xref:System.ServiceModel.InstanceContext> pro každý vytvořený typ singleton nebo pro uživatelem zadaný typ singleton.|  
  
## <a name="see-also"></a>Viz také:

- [Použití relací](../../../../docs/framework/wcf/using-sessions.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Postupy: Řízení vytváření instancí služby](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Souběžnost](../../../../docs/framework/wcf/samples/concurrency.md)
- [Vytváření instancí](../../../../docs/framework/wcf/samples/instancing.md)
- [Relace](../../../../docs/framework/wcf/samples/session.md)
