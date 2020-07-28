---
title: 'Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox'
description: Naučte se používat událost TextChanged ke spuštění metody vždy, když se text v ovládacím prvku TextBox změní v Windows Presentation Foundation aplikaci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166227"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="7b95e-103">Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="7b95e-103">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="7b95e-104">Tento příklad ukazuje jeden ze způsobů, jak použít <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost ke spuštění metody pokaždé, když se <xref:System.Windows.Controls.TextBox> změní text v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="7b95e-104">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="7b95e-105">V třídě kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ovládacího prvku, který obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když se <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost aktivuje.</span><span class="sxs-lookup"><span data-stu-id="7b95e-105">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="7b95e-106">Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.</span><span class="sxs-lookup"><span data-stu-id="7b95e-106">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="7b95e-107">Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="7b95e-107">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="7b95e-108">Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.</span><span class="sxs-lookup"><span data-stu-id="7b95e-108">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="7b95e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b95e-109">Example</span></span>

<span data-ttu-id="7b95e-110">V ovládacím [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] prvku definujícího <xref:System.Windows.Controls.TextBox> ovládací prvek zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atribut s hodnotou, která odpovídá názvu metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7b95e-110">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="7b95e-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b95e-111">Example</span></span>

<span data-ttu-id="7b95e-112">V třídě kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ovládacího prvku, který obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když se <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> událost aktivuje.</span><span class="sxs-lookup"><span data-stu-id="7b95e-112">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="7b95e-113">Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.</span><span class="sxs-lookup"><span data-stu-id="7b95e-113">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="7b95e-114">Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="7b95e-114">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="7b95e-115">Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.</span><span class="sxs-lookup"><span data-stu-id="7b95e-115">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="7b95e-116">Komentáře</span><span class="sxs-lookup"><span data-stu-id="7b95e-116">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="7b95e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b95e-117">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="7b95e-118">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="7b95e-118">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="7b95e-119">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="7b95e-119">RichTextBox Overview</span></span>](richtextbox-overview.md)
