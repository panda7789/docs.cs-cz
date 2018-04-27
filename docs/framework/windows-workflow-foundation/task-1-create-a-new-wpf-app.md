---
title: 'Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd21013331e19fa9e18ad7cbee0a7bb07abaf3d2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
