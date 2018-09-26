---
title: Architektura programování aplikace služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
author: ghogen
ms.openlocfilehash: fbe75d8ec4a677c47a98a5868c4e7e44c95f1d93
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47115006"
---
# <a name="service-application-programming-architecture"></a>Architektura programování aplikace služby
Aplikace služby Windows jsou založeny na třídu, která dědí z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> třídy. Přepište metody z této třídy a definice funkcí pro ně k určení chování služby.  
  
 Hlavní třídy účastnící se vytváření služby jsou:  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> – Můžete přepsat metody ze <xref:System.ServiceProcess.ServiceBase> třídy při vytváření služby a definování kódu k určení, jak funkce služby v tomto zděděné třídy.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> a <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> – použití těchto tříd k instalaci a odinstalaci služby.  
  
 Kromě toho třída s názvem <xref:System.ServiceProcess.ServiceController> slouží k manipulaci s samotné služby. Tato třída není potřebný k vytvoření služby, ale je možné spustit a zastavit službu, předat příkazů a vrátí řadu výčty.  
  
## <a name="defining-your-services-behavior"></a>Definování chování vaší služby  
 Ve své třídě služby přepsání funkcí základní třídy, které určují, co se stane, když je změněn stav služby ve správci řízení služeb. <xref:System.ServiceProcess.ServiceBase> Třída zveřejňuje následující metody, které pokud chcete přidat vlastní chování můžete přepsat.  
  
|Metoda|Přepsání nastavení za účelem|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Určit, jaké akce je třeba provést při spuštění služby. Psaní kódu v tomto postupu pro vaši službu provádět užitečnou práci.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Určit, co se stane, když vaše služba je pozastavena.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Určit, co se stane, když vaše služba se zastaví.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Určit, co se stane, když vaše služba se obnoví normální fungování po pozastavení.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Určit, co se stane před systému vypíná, pokud vaše služba je spuštěná v daném čase.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Určit, co se stane, když služby obdrží vlastní příkaz. Další informace o vlastních příkazů najdete v tématu MSDN online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Označuje, jak služba by měl odpovědět při přijetí události řízení spotřeby, například při nízkém stavu baterie nebo pozastavené operace.|  
  
> [!NOTE]
>  Tyto metody představují stavy, které služba prochází přes v průběhu své životnosti; přechody služby z jednoho stavu do druhého. Například se nikdy získat službu na <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> příkazu před <xref:System.ServiceProcess.ServiceBase.OnStart%2A> byla volána.  
  
 Existuje několik dalších vlastností a metod, které jsou zajímavé. Zde jsou některé z nich:  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A> Metodu <xref:System.ServiceProcess.ServiceBase> třídy. Toto je hlavní vstupní bod pro službu. Pokud vytvoříte službu pomocí šablony služby Windows, vloží se kód ve vaší aplikaci `Main` metoda ke spuštění služby. Tento kód vypadá takto:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Tyto příklady používají pole typu <xref:System.ServiceProcess.ServiceBase>, do které každá služba, která obsahuje vaše aplikace je možné přidat, a pak všechny služby, lze spustit společně. Pokud vytváříte pouze jedinou službou, ale můžete zvolit použití pole a jednoduše deklarujte nový objekt z <xref:System.ServiceProcess.ServiceBase> a pak ho spusťte. Příklad najdete v tématu [postupy: zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Řadu vlastnosti <xref:System.ServiceProcess.ServiceBase> třídy. Tyto určují, jaké metody lze volat pro vaši službu. Například, když <xref:System.ServiceProcess.ServiceBase.CanStop%2A> je nastavena na `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> nelze volat metodu pro vaši službu. Když <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> je nastavena na `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> a <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> metody lze volat. Když nastavíte jednu z těchto vlastností na `true`, pak by měl přepsat a definovat zpracování pro související metody.  
  
    > [!NOTE]
    >  Vaše služba musí přepsat alespoň <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> užitečnost.  
  
 Můžete také použít komponenty s názvem <xref:System.ServiceProcess.ServiceController> a komunikovat s ním řídit chování existující služby.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
