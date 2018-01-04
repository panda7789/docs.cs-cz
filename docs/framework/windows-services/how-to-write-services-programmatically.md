---
title: "Postupy: Zápis služeb prostřednictvím kódu programu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: cdb9c7bba564b71bfba86076218e48610cf73076
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-services-programmatically"></a>Postupy: Zápis služeb prostřednictvím kódu programu
Pokud se rozhodnete použít projektu šablony služeb systému Windows, můžete napsat vlastní služby nastavením dědičnosti a dalších prvků infrastruktury sami. Při vytváření služby prostřednictvím kódu programu, je třeba provést několik kroků, které pro vás by jinak zpracovat šablony:  
  
-   Třídě služby je potřeba nastavit dědění z <xref:System.ServiceProcess.ServiceBase> třídy.  
  
-   Musíte vytvořit `Main` metodu pro projekt služby, který definuje spuštění služeb a volání <xref:System.ServiceProcess.ServiceBase.Run%2A> metoda na ně.  
  
-   Je nutné přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedury a vyplňte kód, chcete, aby se spouštěly.  
  
### <a name="to-write-a-service-programmatically"></a>Pro zápis služby prostřednictvím kódu programu  
  
1.  Vytvořit prázdný projekt a vytvořte odkaz na obory názvů potřeby pomocí následujících kroků:  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a klikněte na tlačítko **přidat odkaz na**.  
  
    2.  Na **rozhraní .NET Framework** kartě, přejděte na **System.dll** a klikněte na tlačítko **vyberte**.  
  
    3.  Přejděte na **System.ServiceProcess.dll** a klikněte na tlačítko **vyberte**.  
  
    4.  Click **OK**.  
  
2.  Přidejte třídu a nakonfigurujte ji dědění z <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Přidejte následující kód do konfigurace vaší služby třídy:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Vytvoření `Main` metody pro třídu a použijte jej k definování službu bude obsahovat vlastní třídy; `userService1` je název třídy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Přepsání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a definujte jakékoli zpracovávání chcete dojít, když je spuštěna.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Přepsat jiné metody, které chcete definovat vlastní zpracování a napsat kód, aby určila provedení akcí, kterou služba má provést v každém případu.  
  
7.  Přidejte nezbytné instalační programy pro aplikaci služby. Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Sestavení projektu výběrem **sestavit řešení** z **sestavení** nabídky.  
  
    > [!NOTE]
    >  Není stisknutím klávesy F5 spusťte projekt – služba projektu nelze spustit tímto způsobem.  
  
9. Vytvoření projektu instalace a vlastní akce pro instalaci služby. Příklad, naleznete v části [návod: vytváření aplikace služby systému Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Nainstalujte službu. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Postupy: Protokolování informací o službách](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
