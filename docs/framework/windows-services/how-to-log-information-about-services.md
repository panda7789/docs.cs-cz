---
title: 'Postupy: Zaznamenávání informací o službách'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: 5556b83346aba5bc48eddb930dedc56f4786bdb5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401391"
---
# <a name="how-to-log-information-about-services"></a>Postupy: Zaznamenávání informací o službách
Všechny projekty služeb Windows ve výchozím nastavení, mají možnost pracovat v protokolu událostí aplikace a do ní zapisovat informace a výjimek. Můžete použít <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost určit, jestli chcete tuto funkci ve vaší aplikaci. Ve výchozím nastavení je protokolování zapnuto na jakoukoli službu, které vytvoříte pomocí šablony projektu služby Windows. Můžete použít statické formu <xref:System.Diagnostics.EventLog> třídu pro zápis služby informace do protokolu bez nutnosti vytvářet instance <xref:System.Diagnostics.EventLog> komponenta nebo ruční registraci zdroje.  
  
 Instalační program pro vaši službu automaticky zaregistruje každé služby ve vašem projektu jako platný zdroj události protokolu aplikace na počítači, kde je služba nainstalována, když je vypnuté protokolování. Služba protokoluje informace pokaždé, když službu je spuštění, zastavení, pozastaveno, obnovení, nainstalované nebo odinstalovat. Také zaznamenává všechny chyby, ke kterým dochází. Není potřeba psát kód pro zápis položky do protokolu, při použití výchozí chování; Služba zpracovává to pro vás automaticky.  
  
 Pokud chcete zapisovat do protokolu událostí než protokolu aplikace, je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`vytvořit vlastní vlastního protokolu událostí v rámci vašeho kódu služby a registraci služby jako platný zdroj položek pro tento protokol. Pak musíte napsat, že se zobrazí kód pro záznam položky protokolu pokaždé, když akce, které vás zajímají.  
  
> [!NOTE]
>  Pokud používáte vlastního protokolu událostí a nakonfigurovat aplikaci služby pro zápis do něj, nesmí pokus o přístup do protokolu událostí před nastavením služby <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti ve vašem kódu. V protokolu událostí musí tato vlastnost hodnotu pro registraci služby jako platný zdroj událostí.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Povolení protokolování událostí výchozí pro vaši službu  
  
-   Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu do `true`.  
  
    > [!NOTE]
    >  Ve výchozím nastavení, tato vlastnost nastavena na `true`. Není nutné nastavovat to explicitně, pokud nevytváříte složitější zpracování, jako jsou například vyhodnocení podmínky a pak nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> nastavenou na výsledek této podmínky.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Chcete-li zakázat protokolování událostí pro vaši službu  
  
-   Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu do `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Nastavení protokolování do vlastního protokolu  
  
1.  Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`.  
  
    > [!NOTE]
    >  Je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na hodnotu false, aby bylo možné používat vlastní protokol.  
  
2.  Nastavení instance <xref:System.Diagnostics.EventLog> komponentu v aplikaci služby Windows.  
  
3.  Vytvoření vlastního protokolu pomocí volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metoda a určení zdrojový řetězec a název protokolu souboru chcete vytvořit.  
  
4.  Nastavte <xref:System.Diagnostics.EventLog.Source%2A> vlastnost <xref:System.Diagnostics.EventLog> instanci komponenty zdrojový řetězec, který jste vytvořili v kroku 3.  
  
5.  Zapisovat položky díky přístupu <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodu na <xref:System.Diagnostics.EventLog> instance komponenty.  
  
     Následující kód ukazuje, jak nastavit protokolování, aby se vlastní protokol.  
  
    > [!NOTE]
    >  V tomto příkladu kódu, instance <xref:System.Diagnostics.EventLog> komponenta má název `eventLog1` (`EventLog1` v jazyce Visual Basic). Pokud jste vytvořili instanci s jiným názvem v kroku 2, kód odpovídajícím způsobem měnit.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
