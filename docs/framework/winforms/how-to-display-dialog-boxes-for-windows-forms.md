---
title: 'Postupy: zobrazení dialogových oken'
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
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739459"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="98f8f-102">Postupy: Zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98f8f-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="98f8f-103">Dialogové okno se zobrazí stejným způsobem jako jakýkoli jiný formulář v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="98f8f-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="98f8f-104">Spouštěcí formulář se při spuštění aplikace automaticky načte.</span><span class="sxs-lookup"><span data-stu-id="98f8f-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="98f8f-105">Chcete-li v aplikaci zobrazit druhý formulář nebo dialogové okno, zadejte kód pro načtení a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="98f8f-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="98f8f-106">Podobně pokud chcete, aby formulář nebo dialogové okno zmizely, napište kód pro uvolnění nebo skrytí.</span><span class="sxs-lookup"><span data-stu-id="98f8f-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="98f8f-107">Zobrazení dialogového okna</span><span class="sxs-lookup"><span data-stu-id="98f8f-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="98f8f-108">Přejděte k obslužné rutině události, pomocí které chcete otevřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="98f8f-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="98f8f-109">K tomu může dojít při výběru příkazu nabídky, při kliknutí na tlačítko nebo při výskytu jakékoli jiné události.</span><span class="sxs-lookup"><span data-stu-id="98f8f-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="98f8f-110">V obslužné rutině události přidejte kód pro otevření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="98f8f-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="98f8f-111">V tomto příkladu se k zobrazení dialogového okna používá událost kliknutí tlačítkem myši:</span><span class="sxs-lookup"><span data-stu-id="98f8f-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
