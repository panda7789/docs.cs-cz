---
title: "Postupy: Zobrazování dialogových oken pro Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46e4d019bbd586c0ed46794f55c65da7bcc657f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="c001c-102">Postupy: Zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c001c-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="c001c-103">Zobrazit dialogové okno stejným způsobem zobrazí všechny formuláře v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c001c-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="c001c-104">Formulář spuštění načte automaticky, když je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c001c-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="c001c-105">Chcete-li druhý formulář nebo dialogové okno se zobrazí v aplikaci, napište kód pro načtení a zobrazit ji.</span><span class="sxs-lookup"><span data-stu-id="c001c-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="c001c-106">Stejně tak aby formulář nebo dialogové okno pole zmizí, zápis kódu pro uvolnění nebo skrytí podokna.</span><span class="sxs-lookup"><span data-stu-id="c001c-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="c001c-107">Chcete-li zobrazit dialogové okno</span><span class="sxs-lookup"><span data-stu-id="c001c-107">To display a dialog box</span></span>  
  
1.  <span data-ttu-id="c001c-108">Přejděte k obslužné rutině událostí, pro který chcete otevřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c001c-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="c001c-109">Tato situace může nastat, pokud je vybraný příkaz nabídky, při kliknutí na tlačítko nebo při výskytu další události.</span><span class="sxs-lookup"><span data-stu-id="c001c-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2.  <span data-ttu-id="c001c-110">V obslužné rutině události přidejte kód k otevření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="c001c-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="c001c-111">V tomto příkladu se používá události kliknutí na tlačítko zobrazit dialogové okno:</span><span class="sxs-lookup"><span data-stu-id="c001c-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
