---
title: "ImageList – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a913de1a6808c7e600a4f28ed58dedf93506466b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imagelist-component-overview-windows-forms"></a><span data-ttu-id="435bb-102">ImageList – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="435bb-102">ImageList Component Overview (Windows Forms)</span></span>
<span data-ttu-id="435bb-103">Windows Forms <xref:System.Windows.Forms.ImageList> komponenta se používá k ukládání Image, které pak lze zobrazit pomocí ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="435bb-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is used to store images, which can then be displayed by controls.</span></span> <span data-ttu-id="435bb-104">Seznam obrázků můžete napsat kód pro jeden a konzistentní katalog bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="435bb-104">An image list allows you to write code for a single, consistent catalog of images.</span></span> <span data-ttu-id="435bb-105">Například můžete otáčení obrázků, na které se zobrazí <xref:System.Windows.Forms.Button> řízení jednoduše tak, že změna na tlačítko <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> nebo <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="435bb-105">For example, you can rotate images displayed by a <xref:System.Windows.Forms.Button> control simply by changing the button's <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> or <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> property.</span></span> <span data-ttu-id="435bb-106">Stejný seznam bitové kopie můžete taky přidružit více ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="435bb-106">You can also associate the same image list with multiple controls.</span></span> <span data-ttu-id="435bb-107">Například, pokud používáte obě <xref:System.Windows.Forms.ListView> řízení a <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazí stejný seznam souborů, změna na ikonu v seznamu obrázků, které způsobí, že na ikonu Nový se zobrazí v obou zobrazeních.</span><span class="sxs-lookup"><span data-stu-id="435bb-107">For example, if you are using both a <xref:System.Windows.Forms.ListView> control and a <xref:System.Windows.Forms.TreeView> control to display the same list of files, changing a file's icon in the image list will cause the new icon to appear in both views.</span></span>  
  
## <a name="using-imagelist-with-controls"></a><span data-ttu-id="435bb-108">Použití seznamu obrázků s ovládacími prvky</span><span class="sxs-lookup"><span data-stu-id="435bb-108">Using ImageList with Controls</span></span>  
 <span data-ttu-id="435bb-109">Můžete použít seznamu obrázků s libovolný ovládací prvek, který má `ImageList` vlastnost – nebo u <xref:System.Windows.Forms.ListView> řízení, <xref:System.Windows.Forms.ListView.SmallImageList%2A> a <xref:System.Windows.Forms.ListView.LargeImageList%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="435bb-109">You can use an image list with any control that has an `ImageList` property — or in the case of the <xref:System.Windows.Forms.ListView> control, <xref:System.Windows.Forms.ListView.SmallImageList%2A> and <xref:System.Windows.Forms.ListView.LargeImageList%2A> properties.</span></span> <span data-ttu-id="435bb-110">Ovládací prvky, které může být spojeno s seznamu obrázků zahrnují: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, a <xref:System.Windows.Forms.Label> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="435bb-110">The controls that can be associated with an image list include: the <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, and <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="435bb-111">Chcete-li přidružit seznamu obrázků s ovládacím prvkem, nastavte ovládacího prvku `ImageList` vlastnost na název <xref:System.Windows.Forms.ImageList> součásti.</span><span class="sxs-lookup"><span data-stu-id="435bb-111">To associate the image list with a control, set the control's `ImageList` property to the name of the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="435bb-112">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="435bb-112">Key Properties</span></span>  
 <span data-ttu-id="435bb-113">Klíčové vlastnosti <xref:System.Windows.Forms.ImageList> součást <xref:System.Windows.Forms.ImageList.Images%2A>, obsahující obrázky, které má být používána přidruženého ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="435bb-113">The key property of the <xref:System.Windows.Forms.ImageList> component is <xref:System.Windows.Forms.ImageList.Images%2A>, which contains the pictures to be used by the associated control.</span></span> <span data-ttu-id="435bb-114">Každé jednotlivé bitové kopie můžete přistupovat pomocí jeho hodnotu indexu nebo na základě klíče.</span><span class="sxs-lookup"><span data-stu-id="435bb-114">Each individual image can be accessed by its index value or by its key.</span></span> <span data-ttu-id="435bb-115"><xref:System.Windows.Forms.ImageList.ColorDepth%2A> Vlastnost určuje počet barev, které se vykreslují bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="435bb-115">The <xref:System.Windows.Forms.ImageList.ColorDepth%2A> property determines the number of colors that the images are rendered with.</span></span> <span data-ttu-id="435bb-116">Bitové kopie budou zobrazeny všechny na stejnou velikost, nastaven <xref:System.Windows.Forms.ImageList.ImageSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="435bb-116">The images will all be displayed at the same size, set by the <xref:System.Windows.Forms.ImageList.ImageSize%2A> property.</span></span> <span data-ttu-id="435bb-117">Bitové kopie, které jsou větší se přizpůsobí.</span><span class="sxs-lookup"><span data-stu-id="435bb-117">Images that are larger will be scaled to fit.</span></span>  
  
 <span data-ttu-id="435bb-118">Pokud používáte [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], máte přístup k rozsáhlé knihovně standardní bitové kopie, které můžete použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="435bb-118">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use in your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435bb-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="435bb-119">See Also</span></span>  
 <xref:System.Windows.Forms.ImageList>  
 [<span data-ttu-id="435bb-120">Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList</span><span class="sxs-lookup"><span data-stu-id="435bb-120">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
