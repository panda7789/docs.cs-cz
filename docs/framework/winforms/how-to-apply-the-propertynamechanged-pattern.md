---
title: 'Postupy: Použití vzoru PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 889a7f5f7a84db378acaa88b717b6011f1a3dfdc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703475"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="cbb9e-102">Postupy: Použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="cbb9e-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="cbb9e-103">Následující příklad kódu ukazuje, jak použít *PropertyName*změněné vzor, který má vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="cbb9e-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="cbb9e-104">Tento model použijte při implementaci vlastní ovládací prvky, které se používají s modulem Windows Forms datové vazby.</span><span class="sxs-lookup"><span data-stu-id="cbb9e-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbb9e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbb9e-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbb9e-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cbb9e-106">Compiling the Code</span></span>  
 <span data-ttu-id="cbb9e-107">Chcete-li zkompilovat v předchozím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="cbb9e-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="cbb9e-108">Vložte kód do prázdný soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="cbb9e-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="cbb9e-109">Je nutné použít vlastní ovládací prvek na formuláři Windows, který obsahuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="cbb9e-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb9e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbb9e-110">See also</span></span>
- [<span data-ttu-id="cbb9e-111">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="cbb9e-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)
- [<span data-ttu-id="cbb9e-112">Oznámení změn v datové vazbě Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbb9e-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="cbb9e-113">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="cbb9e-113">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
