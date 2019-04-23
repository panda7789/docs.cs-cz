---
title: 'Postupy: Změna ohraničení Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: d2e5dd761b2422f6d7e92e7bb97dbdf425b8fedf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080108"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="b3866-102">Postupy: Změna ohraničení Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3866-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="b3866-103">Máte několik stylů ohraničení lze vybírat při určování vzhled a chování formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="b3866-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="b3866-104">Pomocí změny <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost, můžete řídit chování změny velikosti ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="b3866-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="b3866-105">Kromě toho nastavení <xref:System.Windows.Forms.Form.FormBorderStyle%2A> má vliv na způsob zobrazení záhlaví a co tlačítka se může zobrazit na to.</span><span class="sxs-lookup"><span data-stu-id="b3866-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="b3866-106">Další informace naleznete v tématu <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="b3866-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="b3866-107">Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3866-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="b3866-108">Viz také [jak: Změna ohraničení Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b3866-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="b3866-109">Chcete-li nastavit styl ohraničení Windows Forms prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b3866-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="b3866-110">Nastavte <xref:System.Windows.Forms.Form.FormBorderStyle%2A> nastavte požadovaný styl.</span><span class="sxs-lookup"><span data-stu-id="b3866-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="b3866-111">Následující příklad kódu nastaví styl ohraničení tvaru `DlgBx1` k <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="b3866-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="b3866-112">Viz také [jak: Vytváření dialogových oken během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b3866-112">Also see [How to: Create Dialog Boxes at Design Time](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span></span>  
  
     <span data-ttu-id="b3866-113">Kromě toho pokud jste zvolili styl ohraničení pro formulář, který obsahuje volitelné **minimalizovat** a **Maximalizovat** tlačítka, můžete zadat, jestli má jeden nebo oba z těchto tlačítek funkční.</span><span class="sxs-lookup"><span data-stu-id="b3866-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="b3866-114">Tato tlačítka jsou užitečné, pokud chcete přesně řídit činnost koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="b3866-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="b3866-115">**Minimalizovat** a **Maximalizovat** tlačítka jsou ve výchozím nastavení povolené, a jejich funkce je zpracováván prostřednictvím **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="b3866-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3866-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3866-116">See also</span></span>

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [<span data-ttu-id="b3866-117">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3866-117">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
