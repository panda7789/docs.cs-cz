---
title: Předávání typů v modulu CLR (Common Language Runtime)
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f71b56daf5e8a012a66f60805246b4164d1b0a07
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973017"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="afbff-102">Předávání typů v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="afbff-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="afbff-103">Přesměrování typu umožňuje přesunout typ do jiného sestavení bez nutnosti opětovné kompilace aplikací, které používají původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="afbff-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="afbff-104">Předpokládejme například, že aplikace používá `Example` třídu v sestavení s názvem *Utility. dll*.</span><span class="sxs-lookup"><span data-stu-id="afbff-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="afbff-105">Vývojáři *nástroje Utility. dll* se mohou rozhodnout Refaktorovat sestavení a v procesu, který by mohli `Example` třídu přesunout do jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="afbff-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="afbff-106">Pokud je stará verze souboru *Utility. dll* nahrazena novou verzí *nástroje Utility. dll* a jeho doprovodném sestavením, aplikace `Example` , která třídu používá, se `Example` nezdařila, protože nemůže najít třídu v nové verzi  *Nástroj. dll*.</span><span class="sxs-lookup"><span data-stu-id="afbff-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="afbff-107">Vývojáři *nástroje Utility. dll* se k tomu mohou vyhnout přesměrováním požadavků `Example` pro <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> třídu pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="afbff-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="afbff-108">Pokud byl atribut použit pro novou verzi *nástroje Utility. dll*, požadavky `Example` na třídu jsou předány sestavení, které nyní obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="afbff-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="afbff-109">Stávající aplikace bude nadále fungovat normálně bez nutnosti rekompilace.</span><span class="sxs-lookup"><span data-stu-id="afbff-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afbff-110">V .NET Framework verze 2,0 nemůžete předávané typy ze sestavení napsaných v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="afbff-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="afbff-111">Aplikace napsaná v Visual Basic však může využívat předané typy.</span><span class="sxs-lookup"><span data-stu-id="afbff-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="afbff-112">To znamená, že pokud aplikace používá sestavení kódované v C# nebo C++a typ z tohoto sestavení je předáván do jiného sestavení, Visual Basic aplikace může použít předaný typ.</span><span class="sxs-lookup"><span data-stu-id="afbff-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="afbff-113">Předávané typy</span><span class="sxs-lookup"><span data-stu-id="afbff-113">Forward types</span></span>  
 <span data-ttu-id="afbff-114">Existují čtyři kroky pro předání typu:</span><span class="sxs-lookup"><span data-stu-id="afbff-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="afbff-115">Přesune zdrojový kód pro typ z původního sestavení do cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="afbff-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
   
2. <span data-ttu-id="afbff-116">V sestavení, kde se používá typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="afbff-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="afbff-117">Následující kód ukazuje atribut pro typ s názvem `Example` , který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="afbff-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. <span data-ttu-id="afbff-118">Zkompilujte sestavení, které nyní obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="afbff-118">Compile the assembly that now contains the type.</span></span>  
   
4. <span data-ttu-id="afbff-119">Znovu zkompilujte sestavení, kde se nachází typ, s odkazem na sestavení, které nyní obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="afbff-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="afbff-120">Například pokud kompilujete C# soubor z příkazového řádku, použijte možnost [/Reference (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) a určete sestavení, které obsahuje daný typ.</span><span class="sxs-lookup"><span data-stu-id="afbff-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="afbff-121">V C++Použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje daný typ.</span><span class="sxs-lookup"><span data-stu-id="afbff-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbff-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afbff-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="afbff-123">Předávání typů (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="afbff-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="afbff-124">#using direktiva</span><span class="sxs-lookup"><span data-stu-id="afbff-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
