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
manager: douge
ms.openlocfilehash: a046c62de8789cbe438dcc849ffc23991a803ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513959"
---
# <a name="how-to-log-information-about-services"></a>Postupy: Zaznamenávání informací o službách
Všechny projekty služby systému Windows ve výchozím nastavení, mají možnost využívat v protokolu událostí aplikace a do něj zapisovat informace a výjimky. Můžete použít <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost označující, zda chcete tuto funkci v aplikaci. Ve výchozím nastavení je protokolování zapnuto služby, které vytvoříte pomocí šablony projektu služby systému Windows. Můžete použít statické formu <xref:System.Diagnostics.EventLog> třída pro psaní informace o službě do protokolů, aniž by bylo nutné vytvořit instanci <xref:System.Diagnostics.EventLog> součást nebo ručně zaregistrovat zdroj.  
  
 Instalační program služby automaticky registruje každé služby v projektu jako platný zdroj události protokolu aplikace v počítači, kterém je nainstalována služba, když je zapnuté protokolování. Služba zaznamená do protokolu informace pokaždé, když služba spuštění, zastavení, pozastavena, byl obnoven, nainstalován nebo odinstalovat. Zaznamená také všechny chyby, ke kterým dochází. Není potřeba psaní jakéhokoli kódu službě zapisovat položky protokolu, při použití výchozí chování; Služba zpracovává to pro vás automaticky.  
  
 Pokud chcete zapisovat do protokolu událostí, než v protokolu aplikace, je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`, vytvořte vlastní vlastní protokol událostí v kódu služby a registraci služby jako platný zdroj položek pro tento protokol. Pak musíte napsat kódu k zaznamenání položky do protokolu vždy, když akce, které vás zajímají.  
  
> [!NOTE]
>  Pokud používáte vlastní protokol událostí a konfiguraci aplikace služby pro zápis do, nesmíte pokoušet přístup k protokolu událostí před nastavením služby <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastností v kódu. Protokol událostí, musí tato vlastnost hodnotu k registraci služby jako platný zdroj událostí.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Povolení protokolování událostí výchozí služby  
  
-   Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro příslušné součásti na `true`.  
  
    > [!NOTE]
    >  Ve výchozím nastavení je tato vlastnost nastavena `true`. Není nutné explicitně nastavit Pokud vytváříte složitější zpracování, např. vyhodnocení podmínku a pak nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastností na základě výsledku této podmínky.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Zakázání protokolování událostí pro služby  
  
-   Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro příslušné součásti na `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Nastavení protokolování do vlastní protokolu  
  
1.  Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`.  
  
    > [!NOTE]
    >  Je nutné nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na hodnotu false, aby bylo možné používat vlastní protokol.  
  
2.  Nastavit instanci <xref:System.Diagnostics.EventLog> součásti v aplikaci služby systému Windows.  
  
3.  Vytvořit vlastní protokol voláním <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metoda a zadání zdrojový řetězec a název protokolu soubor chcete vytvořit.  
  
4.  Nastavte <xref:System.Diagnostics.EventLog.Source%2A> vlastnost <xref:System.Diagnostics.EventLog> instanci komponenty zdrojový řetězec, který jste vytvořili v kroku 3.  
  
5.  Zapisovat vaše položky přímým přístupem <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodu <xref:System.Diagnostics.EventLog> instanci součásti.  
  
     Následující kód ukazuje, jak nastavit protokolování do vlastního protokolu.  
  
    > [!NOTE]
    >  V tomto příkladu kódu, instance <xref:System.Diagnostics.EventLog> komponenta má název `eventLog1` (`EventLog1` v jazyce Visual Basic). Pokud jste vytvořili instanci s jiným názvem v kroku 2, změňte kód odpovídajícím způsobem.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
