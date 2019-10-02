---
title: Kódování a model Windows Forms globalizace
ms.date: 03/30/2017
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
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736888"
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="de74c-102">Kódování a model Windows Forms globalizace</span><span class="sxs-lookup"><span data-stu-id="de74c-102">Encoding and Windows Forms Globalization</span></span>

<span data-ttu-id="de74c-103">Model Windows Forms aplikace jsou ve formátu Unicode povoleny, což znamená, že každý znak je reprezentován jedinečným číslem bez ohledu na to, jakou platformu, program nebo jazyk.</span><span class="sxs-lookup"><span data-stu-id="de74c-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="de74c-104">Další informace o kódování Unicode najdete na webu [Unicode Consortium](https://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="de74c-104">For more information about Unicode, see the [Unicode consortium Web site](https://www.unicode.org).</span></span>

## <a name="benefits-of-unicode"></a><span data-ttu-id="de74c-105">Výhody sady Unicode</span><span class="sxs-lookup"><span data-stu-id="de74c-105">Benefits of Unicode</span></span>

<span data-ttu-id="de74c-106">Výhody formulářů s podporou kódování Unicode zahrnují schopnost pracovat se skripty, které jsou jenom Unicode, například Hindština.</span><span class="sxs-lookup"><span data-stu-id="de74c-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="de74c-107">Kromě toho můžete použít více jazyků v jednom formuláři.</span><span class="sxs-lookup"><span data-stu-id="de74c-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="de74c-108">V kódování Unicode jsou všechny znaky dlouhé dva bajty, takže nemusíte nic speciálního dělat k reprezentaci dvoubajtových znaků.</span><span class="sxs-lookup"><span data-stu-id="de74c-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="de74c-109">Můžete také napsat jednu sadu kódu, která bude fungovat na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="de74c-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="de74c-110">Jedná se o změnu z předchozích verzí Visual Basic, ve které jste museli psát jiný kód pro různé platformy, například Windows NT a Windows 98.</span><span class="sxs-lookup"><span data-stu-id="de74c-110">This is a change from previous versions of Visual Basic, in which you had to write different code for different platforms, such as Windows NT and Windows 98.</span></span>

<span data-ttu-id="de74c-111">Některé ovládací prvky ale nepodporují kódování Unicode v edicích Windows 98 a Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="de74c-111">However, certain controls do not support Unicode in Windows 98 and Windows Millennium Edition.</span></span> <span data-ttu-id="de74c-112">Všechny tyto ovládací prvky, které dědí z obecného ovládacího prvku, budou zpracovávat data pomocí znakových stránek Windows jako ANSI.</span><span class="sxs-lookup"><span data-stu-id="de74c-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as ANSI.</span></span> <span data-ttu-id="de74c-113">Jsou to tyto ovládací prvky: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="de74c-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="de74c-114">V důsledku toho nemůžete v těchto ovládacích prvcích na uvedených platformách zobrazit data Unicode.</span><span class="sxs-lookup"><span data-stu-id="de74c-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="de74c-115">V anglickém operačním systému Windows 98 například nemůžete zobrazit japonské znaky.</span><span class="sxs-lookup"><span data-stu-id="de74c-115">For example, you cannot display Japanese characters on an English Windows 98 operating system.</span></span>

<span data-ttu-id="de74c-116">Pro alternativy podporující kódování Unicode do ovládacích prvků <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar> použijte ovládací prvky <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip>, které nahradí tyto starší ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="de74c-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="de74c-117">Chcete-li zachovat podobný vzhled a chování mezi vizuálními prvky v aplikaci, použijte ovládací prvek <xref:System.Windows.Forms.MenuStrip> pro vykreslování nabídek místo <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="de74c-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="de74c-118">Stejně jako <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.MenuStrip> také může zpracovávat a zobrazovat znaky Unicode.</span><span class="sxs-lookup"><span data-stu-id="de74c-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>

## <a name="see-also"></a><span data-ttu-id="de74c-119">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="de74c-119">See also</span></span>

- [<span data-ttu-id="de74c-120">Globalizace model Windows Formsch aplikací</span><span class="sxs-lookup"><span data-stu-id="de74c-120">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
