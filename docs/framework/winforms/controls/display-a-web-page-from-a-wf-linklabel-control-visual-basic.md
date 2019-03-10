---
title: 'Postupy: Zobrazení webové stránky z ovládacího prvku Windows Forms LinkLabel (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 7e80dba9cd43385be016506ac2a7e887a68dedf2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705226"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="fce70-102">Postupy: Zobrazení webové stránky z ovládacího prvku Windows Forms LinkLabel (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fce70-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="fce70-103">Tento příklad zobrazuje webovou stránku ve výchozím prohlížeči, když uživatel klikne na tlačítko Windows Forms <xref:System.Windows.Forms.LinkLabel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fce70-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce70-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fce70-104">Example</span></span>  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fce70-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fce70-105">Compiling the Code</span></span>  
 <span data-ttu-id="fce70-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="fce70-106">This example requires:</span></span>  
  
-   <span data-ttu-id="fce70-107">Formuláře Windows s názvem `Form1`.</span><span class="sxs-lookup"><span data-stu-id="fce70-107">A Windows Form named `Form1`.</span></span>  
  
-   <span data-ttu-id="fce70-108">A <xref:System.Windows.Forms.LinkLabel> ovládací prvek s názvem `LinkLabel1`.</span><span class="sxs-lookup"><span data-stu-id="fce70-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
-   <span data-ttu-id="fce70-109">Aktivní připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="fce70-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fce70-110">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fce70-110">.NET Framework Security</span></span>  
 <span data-ttu-id="fce70-111">Volání <xref:System.Diagnostics.Process.Start%2A> metoda vyžaduje úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="fce70-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="fce70-112">Další informace naleznete v tématu <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="fce70-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce70-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fce70-113">See also</span></span>
- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="fce70-114">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="fce70-114">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
