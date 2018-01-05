---
title: "Kódování a globalizace Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25f4f7206b68e961f3c09a488af643ad5d0a4fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="2f361-102">Kódování a globalizace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f361-102">Encoding and Windows Forms Globalization</span></span>
<span data-ttu-id="2f361-103">Aplikace Windows Forms jsou zcela kódování Unicode, což znamená, že každý znak je reprezentována jedinečné číslo, bez ohledu na to, jakou platformu, program nebo jazyk.</span><span class="sxs-lookup"><span data-stu-id="2f361-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="2f361-104">Další informace o kódování Unicode, najdete v článku [Unicode consortium webu](http://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="2f361-104">For more information about Unicode, see the [Unicode consortium Web site](http://www.unicode.org).</span></span>  
  
## <a name="benefits-of-unicode"></a><span data-ttu-id="2f361-105">Výhody kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="2f361-105">Benefits of Unicode</span></span>  
 <span data-ttu-id="2f361-106">Příklady výhod formuláře s podporou Unicode schopnost pracovat s skripty, které jsou výhradně kódování Unicode, jako je například Hindská.</span><span class="sxs-lookup"><span data-stu-id="2f361-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="2f361-107">Kromě toho můžete použít více jazyků na jednoho formuláře.</span><span class="sxs-lookup"><span data-stu-id="2f361-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="2f361-108">V kódu Unicode jsou všechny znaky dva bajty, aby bylo možné žádné speciální úsilí představují dvoubajtové znaky.</span><span class="sxs-lookup"><span data-stu-id="2f361-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="2f361-109">Je také možné zapsat jednu sadu kód, který bude fungovat na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="2f361-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="2f361-110">Jedná se o změnu z předchozích verzí [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ve které jste měli k zápisu jiný kód pro různé platformy, jako je například systému Windows NT a [!INCLUDE[win98](../../../../includes/win98-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f361-110">This is a change from previous versions of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], in which you had to write different code for different platforms, such as Windows NT and [!INCLUDE[win98](../../../../includes/win98-md.md)].</span></span>  
  
 <span data-ttu-id="2f361-111">Některé ovládací prvky však nepodporují kódování Unicode v [!INCLUDE[win98](../../../../includes/win98-md.md)] a Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="2f361-111">However, certain controls do not support Unicode in [!INCLUDE[win98](../../../../includes/win98-md.md)] and Windows Millennium Edition.</span></span> <span data-ttu-id="2f361-112">Tyto ovládací prvky, které dědí běžného ovládacího prvku, bude zpracovávat data s Windows znakové stránky, jako [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f361-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span></span> <span data-ttu-id="2f361-113">Tyto ovládací prvky jsou: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, a <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="2f361-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="2f361-114">V důsledku toho nelze zobrazit Unicode data v těchto ovládacích prvků v uvedených platformách.</span><span class="sxs-lookup"><span data-stu-id="2f361-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="2f361-115">Například nelze zobrazit japonské znaky v angličtině [!INCLUDE[win98](../../../../includes/win98-md.md)] operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2f361-115">For example, you cannot display Japanese characters on an English [!INCLUDE[win98](../../../../includes/win98-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="2f361-116">Kódování Unicode alternativy k <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar> ovládacích prvků, použijte <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky, které nahradí tyto starší ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2f361-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="2f361-117">Chcete-li udržovat podobné vzhled a chování mezi vizuální prvky v aplikaci, použijte <xref:System.Windows.Forms.MenuStrip> řízení pro vykreslování nabídky místo <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="2f361-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="2f361-118">Jako <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> může také zpracovat a zobrazit znaky znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="2f361-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f361-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f361-119">See Also</span></span>  
 [<span data-ttu-id="2f361-120">Globalizace modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f361-120">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
