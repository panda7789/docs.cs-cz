---
title: 'Postupy: Zápis služeb prostřednictvím kódu programu'
description: Nastavení dědičnosti a dalších prvků infrastruktury můžete zobrazit tak, že si nastavili způsob, jak psát služby programově.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 9693e3d387f38319519ab04211d8219fe1e5dda1
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925706"
---
# <a name="how-to-write-services-programmatically"></a>Postupy: Zápis služeb prostřednictvím kódu programu
Pokud se rozhodnete nepoužívat šablonu projektu služby systému Windows, můžete napsat vlastní služby nastavením dědičnosti a dalších prvků infrastruktury sami. Když vytvoříte službu programově, je nutné provést několik kroků, které vám jinak, než to šablona zpracuje:  
  
- Je nutné nastavit třídu služby tak, aby dědila z <xref:System.ServiceProcess.ServiceBase> třídy.  
  
- Musíte vytvořit `Main` metodu pro projekt služby, který definuje služby, které mají být spuštěny, a zavolá <xref:System.ServiceProcess.ServiceBase.Run%2A> metodu na nich.  
  
- Musíte přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy a a vyplnit libovolný kód, který chcete spustit.  
  
### <a name="to-write-a-service-programmatically"></a>Programové vytvoření služby  
  
1. Pomocí následujících kroků vytvořte prázdný projekt a vytvořte odkaz na potřebné obory názvů:  
  
    1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a klikněte na **Přidat odkaz**.  
  
    2. Na kartě **.NET Framework** se posuňte na **System.dll** a klikněte na **Vybrat**.  
  
    3. Posuňte se na **System.ServiceProcess.dll** a klikněte na **Vybrat**.  
  
    4. Klikněte na **OK**.  
  
2. Přidejte třídu a nakonfigurujte ji, aby dědila <xref:System.ServiceProcess.ServiceBase> :  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Přidejte následující kód pro konfiguraci třídy služby:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. Vytvořte `Main` metodu pro třídu a použijte ji k definování služby, kterou bude třída obsahovat; `userService1` je název třídy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Přepište <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu a definujte jakékoli zpracování, které má být provedeno při spuštění služby.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. Přepište jakékoli jiné metody, pro které chcete definovat vlastní zpracování, a napište kód, který určí akce, které by měla služba provádět v každém případě.  
  
7. Přidejte nezbytné instalační programy pro aplikaci služby. Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).  
  
8. Sestavte projekt výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .  
  
    > [!NOTE]
    > Netiskněte klávesu F5 pro spuštění projektu – projekt služby nemůžete tímto způsobem spustit.  
  
9. Vytvořte projekt instalace a vlastní akce pro instalaci služby. Příklad naleznete v tématu [Návod: Vytvoření aplikace služby systému Windows v Návrháři komponent](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Nainstalujte službu. Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Viz také

- [Představení aplikací spouštěných jako služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: Vytváření služeb systému Windows](how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md)
- [Postupy: Zaznamenávání informací o službách](how-to-log-information-about-services.md)
- [Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
