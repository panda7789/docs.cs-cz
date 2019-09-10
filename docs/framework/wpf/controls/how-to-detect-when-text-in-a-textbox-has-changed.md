---
title: 'Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855619"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="6ab5a-102">Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="6ab5a-102">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="6ab5a-103">Tento příklad ukazuje jeden ze <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> způsobů, jak použít událost ke spuštění metody pokaždé, když se změní text <xref:System.Windows.Controls.TextBox> v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="6ab5a-104">V třídě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu na pozadí <xref:System.Windows.Controls.TextBox> ovládacího prvku, který obsahuje ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se událost aktivuje.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="6ab5a-105">Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="6ab5a-106">Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="6ab5a-107">Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-107">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="6ab5a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ab5a-108">Example</span></span>

<span data-ttu-id="6ab5a-109">V ovládacím <xref:System.Windows.Controls.TextBox> prvku definujícího ovládací prvek zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atribut s hodnotou, která odpovídá názvu metody obslužné rutiny události. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ab5a-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="6ab5a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ab5a-110">Example</span></span>

<span data-ttu-id="6ab5a-111">V třídě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu na pozadí <xref:System.Windows.Controls.TextBox> ovládacího prvku, který obsahuje ovládací prvek, který chcete monitorovat, vložte metodu, která bude volána vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se událost aktivuje.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="6ab5a-112">Tato metoda musí mít signaturu, která odpovídá tomu, co očekává <xref:System.Windows.Controls.TextChangedEventHandler> delegát.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="6ab5a-113">Obslužná rutina události se volá vždycky, když se <xref:System.Windows.Controls.TextBox> změní obsah ovládacího prvku, a to buď uživatelem, nebo programově.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="6ab5a-114">Tato událost je aktivována při <xref:System.Windows.Controls.TextBox> vytvoření ovládacího prvku a jeho prvotním vyplnění textem.</span><span class="sxs-lookup"><span data-stu-id="6ab5a-114">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="6ab5a-115">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6ab5a-115">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="6ab5a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ab5a-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="6ab5a-117">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="6ab5a-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="6ab5a-118">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="6ab5a-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
