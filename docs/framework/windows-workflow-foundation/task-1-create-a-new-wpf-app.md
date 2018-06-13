---
title: 'Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 5576d6f893aa405d454758387334b85a473b0c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517946"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation
V této úloze, vytvoříte prázdnou aplikaci Windows Presentation Foundation (WPF) pomocí šablony sady Visual Studio aplikace WPF a přidáte odkazy na příslušné [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sestavení pracovního postupu.  
  
### <a name="to-create-the-wpf-application-project"></a>Chcete-li vytvořit projekt aplikace WPF  
  
1.  Otevřete Visual Studio a na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
2.  V **nový projekt** dialogovém okně vyberte buď **Visual C#** nebo **jazyka Visual Basic** z **nainstalovaných šablonách** podokna na levé straně do pole. Pokud jazyk podle vašeho výběru nezobrazí, podívejte se do části **jiné jazyky**.  
  
3.  Vyberte **Windows** v **nainstalovaných šablonách** podokně.  
  
4.  V tomto horním podokně, potvrďte, že (výchozí hodnota) **rozhraní .NET Framework 4** byl vybraný v rozevíracím seznamu a pak vyberte **aplikaci WPF**.  
  
5.  Nastavte na název projektu do **HostingApplication** v dolní části okna.  
  
6.  Název řešení nastavte **RehostingTheDesigner**.  
  
7.  Klikněte na tlačítko **OK** vytvořit projekt aplikace. Visual Studio vytvoří základní uživatelské rozhraní WPF pro vaši aplikaci a obsahuje odpovídající XAML a soubory kódu.  
  
8.  Přidejte odkazy na **WorkflowModel** sestavení. Chcete-li to provést, v **Průzkumníku řešení**, klikněte pravým tlačítkem myši **HostingApplication** projektu a vyberte **přidat odkaz na**.  
  
9. V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET** podržte stisknutou klávesu CTRL, vyberte následující sestavení a pak klikněte na tlačítko **OK**:  
  
    -   Systém.  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Click **OK**.  
  
11. V tématu [úloha 2: hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) se dozvíte, jak k hostování plátna návrháře návrhu pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Změna hostování Návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Úkol 2: Hostování Návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
