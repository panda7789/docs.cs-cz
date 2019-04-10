---
title: 'Postupy: Zápis služeb prostřednictvím kódu programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: baa7655481c24ebe96b76a0accbff63b6965a021
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328423"
---
# <a name="how-to-write-services-programmatically"></a>Postupy: Zápis služeb prostřednictvím kódu programu
Pokud se rozhodnete nepoužívat šablonu projektu služby Windows, můžete napsat vlastní služby nastavením dědičnosti a další prvky infrastruktury sami. Když vytvoříte službu prostřednictvím kódu programu, je třeba provést několik kroků, které pro vás by jinak zpracovat šablonu:  
  
-   Třída vaší služby musíte nastavit dědění z <xref:System.ServiceProcess.ServiceBase> třídy.  
  
-   Je nutné vytvořit `Main` metodu pro projekt služby, který definuje spuštění služeb a volání <xref:System.ServiceProcess.ServiceBase.Run%2A> metoda na ně.  
  
-   Je nutné přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy a vyplňte jakýkoli kód, který chcete jejich spuštění.  
  
### <a name="to-write-a-service-programmatically"></a>Pro zápis služby prostřednictvím kódu programu  
  
1. Vytvořit prázdný projekt a vytvořte odkaz na nezbytné oborů názvů pomocí následujících kroků:  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a klikněte na **přidat odkaz**.  
  
    2.  Na **rozhraní .NET Framework** kartu, přejděte k položce **System.dll** a klikněte na tlačítko **vyberte**.  
  
    3.  Přejděte k položce **System.ServiceProcess.dll** a klikněte na tlačítko **vyberte**.  
  
    4.  Klikněte na **OK**.  
  
2. Přidejte třídu a nakonfigurovat, aby dědí <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Přidejte následující kód do konfigurace vaší služby třídy:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. Vytvoření `Main` metody pro třídu a použijte k definování service bude obsahovat vaše třída; `userService1` je název třídy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a definujte zpracování chcete dojít, když je vaše služba spuštěná.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. Přepište všechny jiné metody, které chcete definovat vlastní zpracování a zápis kódu určete akce, které služba zabere v každém případě.  
  
7. Přidejte nezbytné instalační programy pro aplikaci služby. Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8. Sestavte projekt výběrem **sestavit řešení** z **sestavení** nabídky.  
  
    > [!NOTE]
    >  Nepoužívejte klávesu F5 ke spuštění projektu – tímto způsobem nelze spustit projekt služby.  
  
9. Vytvoření projektu instalace a vlastní akce pro instalaci vaší služby. Příklad najdete v tématu [názorný postup: Aplikace v Návrháři součástí vytváření Windows služby](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Nainstalujte službu. Další informace najdete v tématu [jak: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Představení aplikací spouštěných jako služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Postupy: Zaznamenávání informací o službách](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [Návod: Vytvoření aplikace služby Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
