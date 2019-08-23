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
ms.openlocfilehash: 1ffc698910fe722fe761c62b87b059068d5f243f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935523"
---
# <a name="how-to-log-information-about-services"></a>Postupy: Zaznamenávání informací o službách
Ve výchozím nastavení mají všechny projekty služby systému Windows schopnost pracovat s protokolem událostí aplikace a zapisovat do něj informace a výjimky. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> Vlastnost můžete použít k určení, zda chcete tuto funkci ve vaší aplikaci. Ve výchozím nastavení je protokolování zapnuté pro každou službu, kterou vytvoříte pomocí šablony projektu služby systému Windows. Můžete použít statickou formu <xref:System.Diagnostics.EventLog> třídy k zápisu informací o službě do protokolu bez nutnosti vytvořit instanci <xref:System.Diagnostics.EventLog> komponenty nebo ručně zaregistrovat zdroj.  
  
 Instalační program pro vaši službu automaticky zaregistruje každou službu v projektu jako platný zdroj událostí s protokolem aplikace v počítači, kde je služba nainstalovaná, pokud je zapnuté protokolování. Služba protokoluje informace pokaždé, když je služba spuštěná, zastavená, pozastavená, obnovená, nainstalovaná nebo odinstalovaná. Také protokoluje všechny chyby, ke kterým dojde. Pokud používáte výchozí chování, nemusíte psát žádný kód pro zápis položek do protokolu. Služba to zpracuje automaticky.  
  
 Pokud chcete zapisovat do protokolu událostí, který je jiný než protokol aplikace, musíte nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost na `false`, vytvořit vlastní protokol událostí v rámci kódu služby a zaregistrovat službu jako platný zdroj záznamů pro tento protokol. Pak musíte napsat kód pro záznam záznamů do protokolu pokaždé, když se vyskytne akce, které vás zajímá.  
  
> [!NOTE]
> Pokud použijete vlastní protokol událostí a nakonfigurujete k zápisu do aplikace služby, nemusíte se před nastavením <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti služby v kódu pokoušet o přístup k protokolu událostí. Protokol událostí potřebuje tuto hodnotu vlastnosti k registraci vaší služby jako platného zdroje událostí.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Povolení protokolování výchozích událostí pro vaši službu  
  
- Nastavte vlastnost pro komponentu na `true`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>  
  
    > [!NOTE]
    > Ve výchozím nastavení je tato vlastnost nastavena na `true`hodnotu. Tuto možnost nemusíte explicitně nastavovat, pokud nevytváříte komplexnější zpracování, jako je například vyhodnocení podmínky a nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnosti na základě výsledku této podmínky.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Zakázání protokolování událostí pro vaši službu  
  
- Nastavte vlastnost pro komponentu na `false`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Nastavení protokolování do vlastního protokolu  
  
1. Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost `false`.  
  
    > [!NOTE]
    > Aby bylo možné <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> použít vlastní protokol, je nutné nastavit hodnotu false.  
  
2. Nastavení instance <xref:System.Diagnostics.EventLog> komponenty v aplikaci služby systému Windows.  
  
3. Vytvořte vlastní protokol voláním <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody a zadáním zdrojového řetězce a názvu souboru protokolu, který chcete vytvořit.  
  
4. <xref:System.Diagnostics.EventLog.Source%2A> Nastavte vlastnost <xref:System.Diagnostics.EventLog> u instance komponenty na zdrojový řetězec, který jste vytvořili v kroku 3.  
  
5. Zapište své položky přístupem k <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodě <xref:System.Diagnostics.EventLog> v instanci komponenty.  
  
     Následující kód ukazuje, jak nastavit protokolování do vlastního protokolu.  
  
    > [!NOTE]
    > V tomto příkladu kódu je instance <xref:System.Diagnostics.EventLog> komponenty pojmenována `eventLog1` (`EventLog1` v Visual Basic). Pokud jste vytvořili instanci s jiným názvem v kroku 2, změňte kód odpovídajícím způsobem.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
