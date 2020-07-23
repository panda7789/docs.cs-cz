---
title: 'Postupy: Zaznamenávání informací o službách'
description: Dozvíte se, jak protokolovat informace o službách. Nastavte vlastnost AutoLog, pokud chcete, aby projekt služby systému Windows spolupracoval s protokolem událostí aplikace.
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
ms.openlocfilehash: 6ebce5464dc25ba4101b3898ee791714f8efc5d6
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925745"
---
# <a name="how-to-log-information-about-services"></a>Postupy: Zaznamenávání informací o službách
Ve výchozím nastavení mají všechny projekty služby systému Windows schopnost pracovat s protokolem událostí aplikace a zapisovat do něj informace a výjimky. Vlastnost můžete použít <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> k určení, zda chcete tuto funkci ve vaší aplikaci. Ve výchozím nastavení je protokolování zapnuté pro každou službu, kterou vytvoříte pomocí šablony projektu služby systému Windows. Můžete použít statickou formu <xref:System.Diagnostics.EventLog> třídy k zápisu informací o službě do protokolu bez nutnosti vytvořit instanci <xref:System.Diagnostics.EventLog> komponenty nebo ručně zaregistrovat zdroj.  
  
 Instalační program pro vaši službu automaticky zaregistruje každou službu v projektu jako platný zdroj událostí s protokolem aplikace v počítači, kde je služba nainstalovaná, pokud je zapnuté protokolování. Služba protokoluje informace pokaždé, když je služba spuštěná, zastavená, pozastavená, obnovená, nainstalovaná nebo odinstalovaná. Také protokoluje všechny chyby, ke kterým dojde. Pokud používáte výchozí chování, nemusíte psát žádný kód pro zápis položek do protokolu. Služba to zpracuje automaticky.  
  
 Pokud chcete zapisovat do protokolu událostí, který je jiný než protokol aplikace, musíte nastavit <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost na `false` , vytvořit vlastní protokol událostí v rámci kódu služby a zaregistrovat službu jako platný zdroj záznamů pro tento protokol. Pak musíte napsat kód pro záznam záznamů do protokolu pokaždé, když se vyskytne akce, které vás zajímá.  
  
> [!NOTE]
> Pokud použijete vlastní protokol událostí a nakonfigurujete k zápisu do aplikace služby, nemusíte se před nastavením vlastnosti služby v kódu pokoušet o přístup k protokolu událostí <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> . Protokol událostí potřebuje tuto hodnotu vlastnosti k registraci vaší služby jako platného zdroje událostí.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Povolení protokolování výchozích událostí pro vaši službu  
  
- Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu na `true` .  
  
    > [!NOTE]
    > Ve výchozím nastavení je tato vlastnost nastavena na hodnotu `true` . Tuto možnost nemusíte explicitně nastavovat, pokud nevytváříte komplexnější zpracování, jako je například vyhodnocení podmínky a nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnosti na základě výsledku této podmínky.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Zakázání protokolování událostí pro vaši službu  
  
- Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost pro komponentu na `false` .  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Nastavení protokolování do vlastního protokolu  
  
1. Nastavte <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> vlastnost na hodnotu `false` .  
  
    > [!NOTE]
    > Aby <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> bylo možné použít vlastní protokol, je nutné nastavit hodnotu false.  
  
2. Nastavení instance <xref:System.Diagnostics.EventLog> komponenty v aplikaci služby systému Windows.  
  
3. Vytvořte vlastní protokol voláním <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody a zadáním zdrojového řetězce a názvu souboru protokolu, který chcete vytvořit.  
  
4. Nastavte <xref:System.Diagnostics.EventLog.Source%2A> vlastnost u <xref:System.Diagnostics.EventLog> instance komponenty na zdrojový řetězec, který jste vytvořili v kroku 3.  
  
5. Zapište své položky přístupem k <xref:System.Diagnostics.EventLog.WriteEntry%2A> metodě v <xref:System.Diagnostics.EventLog> instanci komponenty.  
  
     Následující kód ukazuje, jak nastavit protokolování do vlastního protokolu.  
  
    > [!NOTE]
    > V tomto příkladu kódu <xref:System.Diagnostics.EventLog> je instance komponenty pojmenována `eventLog1` ( `EventLog1` v Visual Basic). Pokud jste vytvořili instanci s jiným názvem v kroku 2, změňte kód odpovídajícím způsobem.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Viz také

- [Představení aplikací spouštěných jako služby systému Windows](introduction-to-windows-service-applications.md)
