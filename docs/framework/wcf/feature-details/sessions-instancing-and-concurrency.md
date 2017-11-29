---
title: "Relace, vytváření instancí a souběžnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f188bc85ae3c2601e98ad29b275c6bb8b698522f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sessions-instancing-and-concurrency"></a>Relace, vytváření instancí a souběžnost
A *relace* existuje korelace všech zpráv odeslaných mezi dva koncové body. *Vytváření instancí* odkazuje na řízení životnost služby uživatelem definované objekty a jejich související <xref:System.ServiceModel.InstanceContext> objekty. *Concurrency* je termín určený k ovládacímu prvku počet vláken, které jsou prováděny v době <xref:System.ServiceModel.InstanceContext> ve stejnou dobu.  
  
 Toto téma popisuje tato nastavení, jak používat a různé interakce mezi nimi.  
  
## <a name="sessions"></a>Relace  
 Když kontraktu služby nastaví <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, tento kontrakt vlastně říká, že všechna volání (který je základní výměny zpráv podporující volání) musí být součástí stejné konverzaci. Pokud kontrakt Určuje, že umožňuje relace, ale nevyžaduje jeden, klienti mohou připojit a buď vytvořit relaci, nebo ne. Pokud relace skončí a a odeslání zprávy pomocí stejných na bázi relací, že se vyvolala výjimku kanálu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]relace mají následující hlavní koncepční funkce:  
  
-   Jsou explicitně iniciované a ukončila příkazem volající aplikace.  
  
-   Zpráv doručených během relace se zpracovávají v pořadí, ve kterém jsou přijaty.  
  
-   Relace korelovat skupinu zpráv k konverzaci. Význam této korelace je abstrakcí. Jeden kanál na bázi relace, například mohou souviset zprávy založené na sdílené síťové připojení, zatímco jiné kanál na bázi relací, mohou souviset zprávy založené na značku sdílené v textu zprávy. Funkce, které může být odvozen z relace závisí na povaze korelaci.  
  
-   Neexistuje žádné obecné datové úložiště přidružené [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relace.  
  
 Pokud jste se seznámili s <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> třídy v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace a funkce, poskytuje, můžete si všimnout, následující rozdíly mezi tento druh relace a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relace:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]relace jsou vždy iniciovaných serverem.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]jsou implicitně neuspořádaný relace.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]relace poskytují mechanismus obecné datové úložiště napříč požadavky.  
  
 Klientské aplikace a aplikace služby spolupracovat s relací různými způsoby. Klientské aplikace zahájení relace a pak přijímat a zpracování zpráv odeslaných v rámci relace. Aplikace služby můžete použít relace jako bod rozšiřitelnosti, chcete-li přidat další chování. K tomu je potřeba pracovat přímo s <xref:System.ServiceModel.InstanceContext> nebo implementaci zprostředkovatele kontextu vlastní instanci.  
  
## <a name="instancing"></a>Vytváření instancí  
 Zřizování instancí chování (nastavit pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost) ovládacích prvků jak <xref:System.ServiceModel.InstanceContext> je vytvořen v odpovědi na příchozí zprávy. Ve výchozím nastavení každý <xref:System.ServiceModel.InstanceContext> je přidružen jeden objekt služby definovaný uživatelem, tak (v případě výchozího) nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost také určuje, vytváření instancí objektů definovaný uživatelem služeb. <xref:System.ServiceModel.InstanceContextMode> Definuje výčet režimů zřizování instancí.  
  
 K dispozici jsou následující režimy zřizování instancí:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nový <xref:System.ServiceModel.InstanceContext> (a proto služby objektu) se vytvoří pro každý požadavek klienta.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nový <xref:System.ServiceModel.InstanceContext> (a proto služby objektu) se vytvoří pro každou novou relaci klienta a udržovat po dobu jeho existence této relace (vyžaduje vazbu, která podporuje relací).  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Jeden <xref:System.ServiceModel.InstanceContext> (a proto služby objektu) zpracuje všechny žádosti klienta po dobu jeho existence aplikace.  
  
 Následující příklad kódu ukazuje výchozí <xref:System.ServiceModel.InstanceContextMode> hodnotu <xref:System.ServiceModel.InstanceContextMode.PerSession> explicitně nastaveno na třídu služby.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 A při <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, jak často <xref:System.ServiceModel.InstanceContext> vydání, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> vlastnosti řízení uvolnění objektu služby.  
  
### <a name="well-known-singleton-services"></a>Známé Singleton služby  
 Jednu variaci na objekty jedna instance služby je někdy užitečné: můžete vytvořit objekt služby sami a vytvořte hostitele služby pomocí tohoto objektu. To pokud chcete udělat, musíte taky nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.InstanceContextMode.Single> nebo po otevření hostitele služby je vyvolána výjimka.  
  
 Použití <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> konstruktor k vytvoření těchto služeb. Poskytuje alternativu k implementaci vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> když chcete zadejte instanci určitý objekt pro použití službou typu singleton. Toto přetížení můžete použít, když vaše typem implementace služby je složité vytvořit (například pokud neimplementuje výchozí veřejný konstruktor bez parametrů).  
  
 Všimněte si, že je-li do tohoto konstruktoru objekt, některé funkce související s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytváření instancí pracovních chování jinak. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je k dispozici instance objektu typu singleton. Podobně se ignoruje jiným mechanismem instance verze. <xref:System.ServiceModel.ServiceHost> Vždy se chová jako kdyby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení InstanceContext objekty  
 Můžete taky řídit, které kanálu relací nebo volání je přidružen který <xref:System.ServiceModel.InstanceContext> objektu tak, že provedete toto přidružení sami.  
  
## <a name="concurrency"></a>Souběžnost  
 Concurrency je ovládací prvek počet vláken v aktivní <xref:System.ServiceModel.InstanceContext> v daném okamžiku. Toto se řídí pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> s <xref:System.ServiceModel.ConcurrencyMode> výčtu.  
  
 K dispozici jsou následující tři režimy souběžnosti:  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>: Každý kontext instance může mít maximálně jedno vlákno zpracování zpráv v kontextu instance současně. Jiná vlákna chtějí používají stejný kontext instance musí zablokuje, dokud se původní vlákno ukončí kontext instance.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Každá instance služby může mít několik vláken zpracování zpráv současně. Implementace služby musí být vláken pro použití tohoto režimu souběžnosti.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Každá instance služby zpracovává jednu zprávu najednou, ale přijímá volání operací vícenásobně. Služba přijímá těchto volání pouze, když se volají pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objekt klienta.  
  
> [!NOTE]
>  Princip fungování a způsob vývoje kód, který je bezpečně používá více než jedno vlákno, může být obtížné úspěšně zapisovat. Před použitím <xref:System.ServiceModel.ConcurrencyMode.Multiple> nebo <xref:System.ServiceModel.ConcurrencyMode.Reentrant> hodnoty, ujistěte se, že služby správně navržena pro tyto režimy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Použití souběžného zpracování se týká zřizování instancí režimu. V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí, souběžnosti není relevantní, protože každá zpráva se zpracuje pomocí nové <xref:System.ServiceModel.InstanceContext> a proto je aktivní v nikdy více než jedno vlákno <xref:System.ServiceModel.InstanceContext>.  
  
 Následující příklad kódu ukazuje nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> vlastnost <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace interakci s InstanceContext nastavení  
 Relace a <xref:System.ServiceModel.InstanceContext> komunikovat, v závislosti na kombinace hodnotu <xref:System.ServiceModel.SessionMode> výčtu ve smlouvě a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> na implementaci služby, který řídí přidružení mezi kanály a konkrétní vlastnost objekty služby.  
  
 V následující tabulce jsou uvedeny výsledek příchozí kanál podpora relací nebo nejsou podporovány relací zadané služby kombinace hodnot <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost.  
  
|Režim InstanceContextMode hodnota|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Chování s kanálu relací: relaci a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />-Chování s nerelační kanál: je vyvolána výjimka.|-Chování s kanálu relací: relaci a <xref:System.ServiceModel.InstanceContext> pro každé volání.<br />-Chování s nerelační kanál: <xref:System.ServiceModel.InstanceContext> pro každé volání.|-Chování s kanálu relací: je vyvolána výjimka.<br />-Chování s nerelační kanál: <xref:System.ServiceModel.InstanceContext> pro každé volání.|  
|PerSession|-Chování s kanálu relací: relaci a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />-Chování s nerelační kanál: je vyvolána výjimka.|-Chování s kanálu relací: relaci a <xref:System.ServiceModel.InstanceContext> pro každý kanál.<br />-Chování s nerelační kanál: <xref:System.ServiceModel.InstanceContext> pro každé volání.|-Chování s kanálu relací: je vyvolána výjimka.<br />-Chování s nerelační kanál: <xref:System.ServiceModel.InstanceContext> pro každé volání.|  
|Single|-Chování s kanálu relací: relaci a jeden <xref:System.ServiceModel.InstanceContext> pro všechna volání.<br />-Chování s nerelační kanál: je vyvolána výjimka.|-Chování s kanálu relací: relaci a <xref:System.ServiceModel.InstanceContext> pro jednotlivý prvek vytvořené nebo definované uživatelem.<br />-Chování s nerelační kanál: <xref:System.ServiceModel.InstanceContext> pro jednotlivý prvek vytvořené nebo definované uživatelem.|-Chování s kanálu relací: je vyvolána výjimka.<br />-Chování s nerelační kanál: <xref:System.ServiceModel.InstanceContext> pro každý vytvořený singleton nebo pro jednotlivý prvek zadaného uživatelem.|  
  
## <a name="see-also"></a>Viz také  
 [Použití relací](../../../../docs/framework/wcf/using-sessions.md)  
 [Postupy: vytvoření služby vyžadující relace](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)  
 [Postupy: vytváření instancí služby Řízení](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)  
 [Souběžnosti](../../../../docs/framework/wcf/samples/concurrency.md)  
 [Vytváření instancí](../../../../docs/framework/wcf/samples/instancing.md)  
 [Relace](../../../../docs/framework/wcf/samples/session.md)
