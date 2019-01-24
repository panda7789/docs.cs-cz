---
title: Relace, vytváření instancí a souběžnost
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 5ccd6fe5e07b2a1bc36b89d1fe14f7990dc7231d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661816"
---
# <a name="sessions-instancing-and-concurrency"></a>Relace, vytváření instancí a souběžnost
A *relace* , že existuje korelace všech zpráv mezi dva koncové body. *Vytváření instancí* odkazuje na řízení životnosti služby uživatelem definované objekty a jejich související <xref:System.ServiceModel.InstanceContext> objekty. *Souběžnost* je termín určený do ovládacího prvku počet vláken v <xref:System.ServiceModel.InstanceContext> ve stejnou dobu.  
  
 Toto téma popisuje nastavení, jak používat a různé interakce mezi nimi.  
  
## <a name="sessions"></a>Relace  
 Pokud kontrakt služby nastaví <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, zda kontrakt říká, že všechna volání (to znamená, základní výměny zpráv, které podporují volání) musí být součástí stejné konverzaci. Pokud kontrakt Určuje, že umožňuje relace, ale nevyžaduje, aby jeden, klienti můžou připojit a buď vytvořit relaci, nebo ne. Pokud relace skončí a zpráva se odesílá přes stejný založeného na relacích, že kanál výjimka je vyvolána výjimka.  
  
 Relace WCF mají koncepční následující hlavní funkce:  
  
-   Jsou explicitně zahájeno a ukončeno volající aplikace.  
  
-   Zprávy doručí během relace se zpracovávají v pořadí, ve kterém jsou přijímány.  
  
-   Relace je možné korelovat skupinu zpráv do konverzace. Význam této korelace je abstrakcí. Například jeden kanál na základě relace mohou souviset zprávy založen na sdílených síťových připojení jiného kanálu založeného na relacích mohou souviset zprávy na základě sdílené značky v textu zprávy. Funkce, které mohou být odvozeny z relace závisí na povaze korelace.  
  
-   Neexistuje žádné úložiště obecná data související s relací WCF.  
  
 Pokud jste se seznámili s <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> třídy v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] poskytuje aplikace a funkce, můžete si všimnout následující rozdíly mezi tento druh relace a relace WCF:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] relace jsou vždy zahajované serverem.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] relace jsou implicitně Neseřazený.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] relace poskytují mechanismus pro ukládání obecná data napříč požadavky.  
  
 Klientské aplikace a aplikace služby pracovat s relacemi různými způsoby. Klientské aplikace zahájení relace přijímat a zpracovávat zprávy odeslané v rámci relace. Aplikace služby slouží k přidání další chování relace jako bod rozšiřitelnosti. To se provádí práci přímo s <xref:System.ServiceModel.InstanceContext> nebo implementaci zprostředkovatele vlastní instance kontextu.  
  
## <a name="instancing"></a>Vytváření instancí  
 Vytvoření instance chování (nastavení s použitím <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost) ovládacích prvků jak <xref:System.ServiceModel.InstanceContext> je vytvořen odpověď na příchozí zprávy. Ve výchozím nastavení každý <xref:System.ServiceModel.InstanceContext> souvisí s jedním objektem služby definovaný uživatelem, takže (ve výchozím nastavení) nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností také řídí vytváření instancí služby uživatelem definované objekty. <xref:System.ServiceModel.InstanceContextMode> Výčet definuje režimy vytvoření instance.  
  
 K dispozici jsou následující režimy vytvoření instance:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nový <xref:System.ServiceModel.InstanceContext> (a tedy service objektu) se vytvoří pro každý požadavek klienta.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nový <xref:System.ServiceModel.InstanceContext> (a tedy service objektu) se vytvoří pro každou novou relaci klienta a Udržovat dobu trvání relace (vyžaduje vazbu, která podporuje relace).  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Jediný <xref:System.ServiceModel.InstanceContext> (a tedy objekt služby) zpracuje všechny žádosti klienta po dobu životnosti aplikace.  
  
 Následující příklad kódu ukazuje výchozí <xref:System.ServiceModel.InstanceContextMode> hodnotu <xref:System.ServiceModel.InstanceContextMode.PerSession> explicitně nastavena na třídu služby.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 A současně přitom <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, jak často <xref:System.ServiceModel.InstanceContext> vydání, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> vlastnosti řídit, že se uvolnilo objekt služby.  
  
### <a name="well-known-singleton-services"></a>Deklarace služeb typu Singleton známé  
 Někdy je užitečné jednu variaci na jednu instanci služby objekty: můžete vytvořit objekt služby, sami a vytvořte hostitele služby pomocí tohoto objektu. Uděláte to tak, musíte taky nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.InstanceContextMode.Single> nebo dojde k výjimce při otevření hostitele služby.  
  
 Použití <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> konstruktor k vytvoření takové služby. Poskytuje alternativu k implementaci vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> když chcete poskytovat konkrétní objekt instance pro použití službou typu singleton. Toto přetížení můžete použít, když váš typ implementace služby se obtížně vytvořit (například pokud neimplementuje výchozí veřejný konstruktor bez parametrů).  
  
 Všimněte si, že je-li do tohoto konstruktoru objekt, jinak fungovat některé funkce související s pro Windows Communication Foundation (WCF) vytváření instancí chování. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je k dispozici instanci typu singleton objektu. Podobně jiný mechanismus uvolnění instance se ignoruje. <xref:System.ServiceModel.ServiceHost> Vždy se chová jako by <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
### <a name="sharing-instancecontext-objects"></a>Třída InstanceContext objekty pro sdílení obsahu  
 Můžete taky řídit, které kanál s relacemi nebo volání je přidružený k který <xref:System.ServiceModel.InstanceContext> objektu pomocí provádí toto přidružení se sami.  
  
## <a name="concurrency"></a>Souběžnost  
 Ovládací prvek počet vláken v aktivní je souběžnost <xref:System.ServiceModel.InstanceContext> v daný okamžik. To je řízen pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> s <xref:System.ServiceModel.ConcurrencyMode> výčtu.  
  
 K dispozici jsou následující tři režimy souběžnosti:  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>: Každý kontext instance může mít maximálně jedno vlákno zpracování zpráv v rámci instance najednou. Ostatní vlákna, které chtějí používat stejný kontext instance musí blokovat, dokud původní vlákno ukončí kontext instance.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Každá instance služby může mít více vláken současně zpracování zpráv. Implementace služby musí být bezpečná pro vlákno pro použití tohoto režimu souběžnosti.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Každá instance služby zpracovává zprávy jeden po druhém, ale přijímá vícenásobně operaci volání. Služba přijímá pouze tato volání při je volání navýšení kapacity pomocí objektu klienta WCF.  
  
> [!NOTE]
>  Principy a vývoji kódu, který bezpečně používá více než jedno vlákno může být obtížné je napsat úspěšně. Před použitím <xref:System.ServiceModel.ConcurrencyMode.Multiple> nebo <xref:System.ServiceModel.ConcurrencyMode.Reentrant> hodnoty, ujistěte se, že je vaše služba správně navržená pro tyto režimy. Další informace naleznete v tématu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Vytvoření instance režimu se týká použití souběžnosti. V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí, souběžnost není odpovídající, protože každá zpráva se zpracuje pomocí nové <xref:System.ServiceModel.InstanceContext> a proto není aktivní v nikdy více než jedno vlákno <xref:System.ServiceModel.InstanceContext>.  
  
 Následující příklad kódu ukazuje nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> vlastnost <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace interakci s InstanceContext nastavení  
 Relace a <xref:System.ServiceModel.InstanceContext> pracovat v závislosti na kombinaci hodnotu <xref:System.ServiceModel.SessionMode> výčtu v kontraktu a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost u implementace služby, které řídí přidružení mezi kanály a konkrétní objekty služby.  
  
 V následující tabulce jsou uvedeny výsledek příchozí kanál podpora relací nebo nenabízí relace zadaná služby kombinace hodnot <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost.  
  
|Režim InstanceContextMode hodnota|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Chování s kanál s relacemi: Relace a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />-Chování nerelační kanálu: Je vyvolána výjimka.|-Chování s kanál s relacemi: Relace a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />-Chování nerelační kanálu: <xref:System.ServiceModel.InstanceContext> Pro každé volání.|-Chování s kanál s relacemi: Je vyvolána výjimka.<br />-Chování nerelační kanálu: <xref:System.ServiceModel.InstanceContext> Pro každé volání.|  
|Hodnotu PerSession|-Chování s kanál s relacemi: Relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />-Chování nerelační kanálu: Je vyvolána výjimka.|-Chování s kanál s relacemi: Relace a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />-Chování nerelační kanálu: <xref:System.ServiceModel.InstanceContext> Pro každé volání.|-Chování s kanál s relacemi: Je vyvolána výjimka.<br />-Chování nerelační kanálu: <xref:System.ServiceModel.InstanceContext> Pro každé volání.|  
|Single|-Chování s kanál s relacemi: Relace a jeden <xref:System.ServiceModel.InstanceContext> pro všechna volání.<br />-Chování nerelační kanálu: Je vyvolána výjimka.|-Chování s kanál s relacemi: Relace a <xref:System.ServiceModel.InstanceContext> pro vytvořené nebo uživatelem zadaného typu singleton.<br />-Chování nerelační kanálu: <xref:System.ServiceModel.InstanceContext> Pro vytvořené nebo uživatelem zadaného typu singleton.|-Chování s kanál s relacemi: Je vyvolána výjimka.<br />-Chování nerelační kanálu: <xref:System.ServiceModel.InstanceContext> Pro každý vytvořený singleton nebo pro jednotlivý prvek zadaného uživatelem.|  
  
## <a name="see-also"></a>Viz také:
- [Použití relací](../../../../docs/framework/wcf/using-sessions.md)
- [Postupy: Vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Postupy: Řízení vytváření instancí služby](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Souběžnost](../../../../docs/framework/wcf/samples/concurrency.md)
- [Vytváření instancí](../../../../docs/framework/wcf/samples/instancing.md)
- [Relace](../../../../docs/framework/wcf/samples/session.md)
