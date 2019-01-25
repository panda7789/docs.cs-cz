---
title: 'Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 39cd901c0129124bece8e8d3a573fd45209cfb00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679406"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation
Při plnění tohoto úkolu Vytvoření prázdné aplikace Windows Presentation Foundation (WPF) pomocí šablony WPF aplikace Visual Studio a přidejte odkazy na příslušné [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sestavení pracovních postupů.  
  
### <a name="to-create-the-wpf-application-project"></a>Vytvoření projektu aplikace WPF  
  
1.  Otevřete sadu Visual Studio a na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogové okno Vyberte buď **Visual C#**  nebo **jazyka Visual Basic** z **nainstalované šablony** podokna na levé straně na straně pole. Pokud jazyk podle vašeho výběru se nezobrazí, podívejte se do části **jiné jazyky**.  
  
3.  Vyberte **Windows** v **nainstalované šablony** podokně.  
  
4.  V horním podokně, ujistěte se, že (výchozí hodnota) **rozhraní .NET Framework 4** vybrané v rozevíracím seznamu a pak vyberte **aplikace WPF**.  
  
5.  Nastavte název projekt tak, aby **HostingApplication** v dolní části okna.  
  
6.  Nastavte název řešení **RehostingTheDesigner**.  
  
7.  Klikněte na tlačítko **OK** vytvoření projektu aplikace. Visual Studio vytvoří základní rozhraní WPF pro vaši aplikaci a obsahuje odpovídající XAML a soubory kódu na pozadí.  
  
8.  Přidání odkazů na **WorkflowModel** sestavení. Chcete-li to provést, v **Průzkumníka řešení**, klikněte pravým tlačítkem myši **HostingApplication** projektu a vyberte **přidat odkaz**.  
  
9. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET** kartu, podržte stisknutou klávesu CTRL, vyberte následující sestavení a pak klikněte na tlačítko **OK**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Klikněte na **OK**.  
  
11. Zobrazit [úloha 2: Hostování návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) informace o hostování pracovního postupu návrháře návrhové plátno.  
  
## <a name="see-also"></a>Viz také:
- [Změna hostování Návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)
- [Úloha 2: Hostování návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
