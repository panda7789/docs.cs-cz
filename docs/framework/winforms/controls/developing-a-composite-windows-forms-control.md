---
title: "Vývoj složeného ovládacího prvku Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b98ba10e1c865417b9e844c4d5c31334f763e1b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="daf0f-102">Vývoj složeného ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="daf0f-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="daf0f-103">Složené ovládací prvek Windows Forms můžete vyvíjet kombinací dalších ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="daf0f-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="daf0f-104">Složené ovládací prvky, které jsou odvozeny od <xref:System.Web.UI.UserControl> se nazývají uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="daf0f-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="daf0f-105">Základní třídy, <xref:System.Windows.Forms.UserControl>, poskytuje směrování pro podřízené prvky, čímž zajišťuje, že podřízené ovládací prvky mohou získat fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="daf0f-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="daf0f-106">Příklad uživatelského ovládacího prvku, naleznete v části <xref:System.Windows.Forms.UserControl> ukázku v [postupy: použití atributů v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="daf0f-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="daf0f-107">Windows Forms designerem v [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] poskytuje rozsáhlou podporu návrhu uživatelské ovládací prvky pro vytváření obsahu.</span><span class="sxs-lookup"><span data-stu-id="daf0f-107">The Windows Forms designer in [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="daf0f-108">[Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-109">[Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-109">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-110">[Návod: Dědění z Windows Forms ovládacího prvku pomocí Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="daf0f-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="daf0f-111">[Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-111">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-112">[Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-112">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-113">[Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-114">[Postupy: Dědění ze třídy Control](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-114">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-115">[Postupy: Otestování běhového chování UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-115">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-116">[Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-116">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-117">[Postupy: Dědění ze třídy UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-117">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-118">[Postupy: Vytváření ovládacích prvků pro Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-118">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-119">[Postupy: Vytváření složených ovládacích prvků](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-119">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-120">[Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-120">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-121">[Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="daf0f-121">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="daf0f-122">[Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-123">[Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="daf0f-124">[Postupy: vytvoření ovládacího prvku Windows Forms, který využívá funkce návrhu](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="daf0f-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf0f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="daf0f-125">See Also</span></span>  
 [<span data-ttu-id="daf0f-126">Postupy: Použití atributů v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="daf0f-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="daf0f-127">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="daf0f-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="daf0f-128">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="daf0f-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
