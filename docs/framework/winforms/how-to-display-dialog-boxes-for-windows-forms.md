---
title: 'Postup: Zobrazení dialogových oken'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181977"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="eb5a8-102">Postupy: Zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb5a8-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="eb5a8-103">Dialogové okno se zobrazí stejným způsobem jako jakýkoli jiný formulář v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="eb5a8-104">Spouštěcí formulář se načte automaticky při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="eb5a8-105">Chcete-li, aby se v aplikaci objevil druhý formulář nebo dialogové okno, napište kód, který se načte a zobrazí.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="eb5a8-106">Podobně chcete-li, aby formulář nebo dialogové okno zmizelo, napište kód pro jeho uvolnění nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="eb5a8-107">Zobrazení dialogového okna</span><span class="sxs-lookup"><span data-stu-id="eb5a8-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="eb5a8-108">Přejděte na obslužnou rutinu události, se kterou chcete dialogové okno otevřít.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="eb5a8-109">K tomu může dojít, když je vybrán příkaz nabídky, klepnutí na tlačítko nebo při výskytu jakékoli jiné události.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="eb5a8-110">V obslužné rutině události přidejte kód a otevřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="eb5a8-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="eb5a8-111">V tomto příkladu se k zobrazení dialogového okna používá událost kliknutí na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="eb5a8-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
