---
title: Předávání typů v modulu Common Language Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1b05a5548beb7e7c1f0ec8e96b6e02350318ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921421"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="4862c-102">Předávání typů v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="4862c-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="4862c-103">Přesměrování typu umožňuje přesunout typ do jiného sestavení bez nutnosti opětovné kompilace aplikací, které používají původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4862c-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="4862c-104">Předpokládejme například, že aplikace používá `Example` třídu v sestavení s názvem. `Utility.dll`</span><span class="sxs-lookup"><span data-stu-id="4862c-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="4862c-105">Vývojáři `Utility.dll` se mohou rozhodnout Refaktorovat sestavení a v procesu, který by mohl `Example` přesunout třídu do jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="4862c-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="4862c-106">Je-li starší verze `Utility.dll` systému nahrazena novou `Utility.dll` verzí a jeho doprovodnou sestavou, aplikace, která `Example` třídu používá, se nezdařila, `Example` protože nemůže `Utility.dll`najít třídu v nové verzi.</span><span class="sxs-lookup"><span data-stu-id="4862c-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="4862c-107">Vývojáři `Utility.dll` se mohou vyhnout předávání požadavků `Example` pro třídu pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="4862c-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="4862c-108">Pokud byl atribut použit pro novou verzi `Utility.dll`nástroje, požadavky `Example` na třídu jsou předány sestavení, které nyní obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="4862c-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="4862c-109">Stávající aplikace bude nadále fungovat normálně bez nutnosti rekompilace.</span><span class="sxs-lookup"><span data-stu-id="4862c-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4862c-110">V .NET Framework verze 2,0 nemůžete předávané typy ze sestavení napsaných v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4862c-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="4862c-111">Aplikace napsaná v Visual Basic však může využívat předané typy.</span><span class="sxs-lookup"><span data-stu-id="4862c-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="4862c-112">To znamená, že pokud aplikace používá sestavení kódované v C# nebo C++a typ z tohoto sestavení je předáván do jiného sestavení, Visual Basic aplikace může použít předaný typ.</span><span class="sxs-lookup"><span data-stu-id="4862c-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="4862c-113">Typy předávání</span><span class="sxs-lookup"><span data-stu-id="4862c-113">Forwarding Types</span></span>  
 <span data-ttu-id="4862c-114">Existují čtyři kroky pro předání typu:</span><span class="sxs-lookup"><span data-stu-id="4862c-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="4862c-115">Přesune zdrojový kód pro typ z původního sestavení do cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="4862c-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2. <span data-ttu-id="4862c-116">V sestavení, kde se používá typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="4862c-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="4862c-117">Následující kód ukazuje atribut pro typ s názvem `Example` , který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="4862c-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. <span data-ttu-id="4862c-118">Zkompilujte sestavení, které nyní obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="4862c-118">Compile the assembly that now contains the type.</span></span>  
  
4. <span data-ttu-id="4862c-119">Znovu zkompilujte sestavení, kde se nachází typ, s odkazem na sestavení, které nyní obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="4862c-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="4862c-120">Například pokud kompilujete C# soubor z příkazového řádku, použijte možnost [/Reference (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) a určete sestavení, které obsahuje daný typ.</span><span class="sxs-lookup"><span data-stu-id="4862c-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="4862c-121">V C++Použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje daný typ.</span><span class="sxs-lookup"><span data-stu-id="4862c-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4862c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4862c-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="4862c-123">Předávání typů (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="4862c-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="4862c-124">#using direktiva</span><span class="sxs-lookup"><span data-stu-id="4862c-124">#using Directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
