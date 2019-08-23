---
title: PrintDocument – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928977"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="6fa4b-102">PrintDocument – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6fa4b-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="6fa4b-103">Komponenta model Windows Forms [PrintDocument](printdocument-component-windows-forms.md) slouží k nastavení vlastností, které popisují, co tisknout a možnost tisku dokumentu v aplikacích určených pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="6fa4b-104">Dá se použít společně s komponentou [PrintDialog](printdialog-component-windows-forms.md) k tomu, aby měla kontrolu nad všemi aspekty tisku dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="6fa4b-105">Práce s komponentou PrintDocument</span><span class="sxs-lookup"><span data-stu-id="6fa4b-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="6fa4b-106">Existují dva z hlavních scénářů, které <xref:System.Drawing.Printing.PrintDocument> zahrnují komponentu:</span><span class="sxs-lookup"><span data-stu-id="6fa4b-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="6fa4b-107">Jednoduché tiskové úlohy, jako je například tisk jednotlivého textového souboru.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="6fa4b-108">V takovém případě <xref:System.Drawing.Printing.PrintDocument> přidejte komponentu do formuláře Windows a pak přidejte programovací logiku, která vytiskne soubor <xref:System.Drawing.Printing.PrintDocument.PrintPage> v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="6fa4b-109">Programovací logika by měla být ukončená <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodou pro tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="6fa4b-110">Tato metoda odesílá <xref:System.Drawing.Graphics> objekt, který je obsažen <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> v vlastnosti <xref:System.Drawing.Printing.PrintPageEventArgs> třídy, do tiskárny.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="6fa4b-111">Příklad, který ukazuje, jak vytisknout textový dokument pomocí <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [How to: Vytiskněte textový soubor s více stránkami v](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="6fa4b-112">Složitější tiskové úlohy, jako je situace, kdy budete chtít znovu použít logiku tisku, kterou jste napsali.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="6fa4b-113">V takovém případě byste měli odvodit <xref:System.Drawing.Printing.PrintDocument> novou komponentu z komponenty a přepsat ji <xref:System.Drawing.Printing.PrintDocument.PrintPage> (viz [přepsání](../../../visual-basic/language-reference/modifiers/overrides.md) pro Visual Basic nebo [přepsání](../../../csharp/language-reference/keywords/override.md) pro C#) události.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="6fa4b-114">Při přidání do formuláře <xref:System.Drawing.Printing.PrintDocument> se komponenta zobrazí v zásobníku v dolní části Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fa4b-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fa4b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fa4b-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="6fa4b-116">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6fa4b-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="6fa4b-117">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="6fa4b-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
