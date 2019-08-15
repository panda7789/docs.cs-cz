---
title: 'Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně'
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 90bbd7df45424f8513598e9d7439d8ae6bf6f52c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040308"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="f2572-102">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="f2572-102">How to: Support COM interop by displaying each Windows Form on its own thread</span></span>

<span data-ttu-id="f2572-103">Problémy s interoperabilitou modelu COM můžete vyřešit zobrazením formuláře ve smyčce zprávy .NET Framework, kterou lze vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f2572-103">You can resolve COM interoperability problems by displaying your form on a .NET Framework message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f2572-104">Chcete-li, aby formulář Windows pracoval správně z klientské aplikace modelu COM, je nutné spustit formulář ve smyčce model Windows Forms zpráv.</span><span class="sxs-lookup"><span data-stu-id="f2572-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="f2572-105">K tomu použijte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="f2572-105">To do this, use one of the following approaches:</span></span>

- <span data-ttu-id="f2572-106">K zobrazení formuláře Windows použijte metodu.<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f2572-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="f2572-107">Další informace najdete v tématu [jak: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody](com-interop-by-displaying-a-windows-form-shadow.md)ShowDialog.</span><span class="sxs-lookup"><span data-stu-id="f2572-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>

- <span data-ttu-id="f2572-108">Zobrazí každý formulář Windows v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="f2572-108">Display each Windows Form on a separate thread.</span></span>

<span data-ttu-id="f2572-109">Existuje Rozsáhlá podpora pro tuto funkci v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2572-109">There is extensive support for this feature in Visual Studio.</span></span>

<span data-ttu-id="f2572-110">Viz [také návod: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))vlastním vlákně.</span><span class="sxs-lookup"><span data-stu-id="f2572-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="f2572-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2572-111">Example</span></span>

<span data-ttu-id="f2572-112">Následující příklad kódu ukazuje, jak zobrazit formulář v samostatném vlákně a volat <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodu pro spuštění model Windows Formsho pumpy zpráv v tomto vlákně.</span><span class="sxs-lookup"><span data-stu-id="f2572-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="f2572-113">Chcete-li použít tento přístup, je nutné zařadit všechna volání do formuláře z nespravované aplikace pomocí <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f2572-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>

<span data-ttu-id="f2572-114">Tento přístup vyžaduje, aby každá instance formuláře běžela ve vlastním vlákně pomocí vlastní smyčky zpráv.</span><span class="sxs-lookup"><span data-stu-id="f2572-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="f2572-115">V jednom vlákně nemůžete mít spuštěnou více než jednu smyčku zpráv.</span><span class="sxs-lookup"><span data-stu-id="f2572-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="f2572-116">Proto nemůžete změnit smyčku zpráv klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2572-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="f2572-117">Můžete však upravit komponentu .NET Framework a spustit nové vlákno, které používá vlastní smyčku zpráv.</span><span class="sxs-lookup"><span data-stu-id="f2572-117">However, you can modify the .NET Framework component to start a new thread that uses its own message loop.</span></span>

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a><span data-ttu-id="f2572-118">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2572-118">Compile the code</span></span>

<span data-ttu-id="f2572-119">Zkompilujte typy `COMForm`, `Form1`a `FormManager` do sestavení s názvem `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="f2572-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="f2572-120">Zaregistrujte sestavení pro zprostředkovatele komunikace s objekty COM pomocí jedné z metod popsaných v tématu [sbalení sestavení pro model COM](../../interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="f2572-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="f2572-121">Nyní můžete použít sestavení a jeho odpovídající soubor knihovny typů (. tlb) v nespravovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="f2572-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="f2572-122">Například můžete použít knihovnu typů jako referenci v spustitelném projektu Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="f2572-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2572-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2572-123">See also</span></span>

- [<span data-ttu-id="f2572-124">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="f2572-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="f2572-125">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="f2572-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="f2572-126">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="f2572-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="f2572-127">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="f2572-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="f2572-128">Přehled modelu Windows Forms a nespravovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="f2572-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
