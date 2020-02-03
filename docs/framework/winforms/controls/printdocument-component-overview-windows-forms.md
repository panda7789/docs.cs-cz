---
title: Přehled komponenty PrintDocument
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728540"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="9f056-102">PrintDocument – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9f056-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="9f056-103">Komponenta model Windows Forms [PrintDocument](printdocument-component-windows-forms.md) slouží k nastavení vlastností, které popisují, co tisknout a možnost tisku dokumentu v aplikacích určených pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="9f056-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="9f056-104">Dá se použít společně s komponentou [PrintDialog](printdialog-component-windows-forms.md) k tomu, aby měla kontrolu nad všemi aspekty tisku dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9f056-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="9f056-105">Práce s komponentou PrintDocument</span><span class="sxs-lookup"><span data-stu-id="9f056-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="9f056-106">Existují dva z hlavních scénářů, které zahrnují komponentu <xref:System.Drawing.Printing.PrintDocument>:</span><span class="sxs-lookup"><span data-stu-id="9f056-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="9f056-107">Jednoduché tiskové úlohy, jako je například tisk jednotlivého textového souboru.</span><span class="sxs-lookup"><span data-stu-id="9f056-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="9f056-108">V takovém případě přidejte komponentu <xref:System.Drawing.Printing.PrintDocument> do formuláře Windows a pak přidejte programovací logiku, která vytiskne soubor v obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="9f056-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="9f056-109">Programovací logika by měla být ukončená metodou <xref:System.Drawing.Printing.PrintDocument.Print%2A> pro tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9f056-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="9f056-110">Tato metoda odesílá objekt <xref:System.Drawing.Graphics>, který je obsažen ve vlastnosti <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs>, do tiskárny.</span><span class="sxs-lookup"><span data-stu-id="9f056-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="9f056-111">Příklad, který ukazuje, jak vytisknout textový dokument pomocí <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete [v tématu How to: Print a multi-Page textový soubor in model Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9f056-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="9f056-112">Složitější tiskové úlohy, jako je situace, kdy budete chtít znovu použít logiku tisku, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="9f056-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="9f056-113">V takovém případě byste měli odvodit novou komponentu z <xref:System.Drawing.Printing.PrintDocument> komponenty a přepsat (viz [přepsání](../../../visual-basic/language-reference/modifiers/overrides.md) pro Visual Basic nebo [přepsání](../../../csharp/language-reference/keywords/override.md) pro C#) události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="9f056-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="9f056-114">Při přidání do formuláře se komponenta <xref:System.Drawing.Printing.PrintDocument> zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f056-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f056-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f056-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="9f056-116">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f056-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="9f056-117">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="9f056-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
