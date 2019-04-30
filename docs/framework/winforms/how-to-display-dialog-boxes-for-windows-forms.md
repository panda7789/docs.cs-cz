---
title: 'Postupy: Zobrazování dialogových oken pro Windows Forms'
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
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802580"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="cdde9-102">Postupy: Zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdde9-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="cdde9-103">Zobrazit dialogové okno stejným způsobem, zobrazit jiné formuláře v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cdde9-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="cdde9-104">Změna formuláře úvodního formuláře načte automaticky při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdde9-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="cdde9-105">Chcete-li druhý formulář nebo dialogové okno se zobrazí v aplikaci, napište kód pro načtení a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cdde9-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="cdde9-106">Podobně aby formulář nebo dialogové okno pole zmizí, napište kód, který uvolnit nebo skryli.</span><span class="sxs-lookup"><span data-stu-id="cdde9-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="cdde9-107">Chcete-li zobrazit dialogové okno</span><span class="sxs-lookup"><span data-stu-id="cdde9-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="cdde9-108">Přejděte do obslužné rutiny události, které chcete otevřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="cdde9-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="cdde9-109">Tomu může dojít, pokud příkaz nabídky je vybraná, po kliknutí na tlačítko, nebo když dojde k jakékoli události.</span><span class="sxs-lookup"><span data-stu-id="cdde9-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="cdde9-110">V obslužné rutině události přidejte kód pro otevření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="cdde9-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="cdde9-111">V tomto příkladu je události kliknutí na tlačítko použít zobrazíte dialogové okno:</span><span class="sxs-lookup"><span data-stu-id="cdde9-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
