---
title: 'Postupy: Odkazování na sestavení se silným názvem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 281cfa6507d293658e436a95a5ded0174154a13c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301019"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="192a9-102">Postupy: Odkazování na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="192a9-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="192a9-103">Proces pro odkazování na typy a prostředky v sestavení se silným názvem je obvykle transparentní.</span><span class="sxs-lookup"><span data-stu-id="192a9-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="192a9-104">Odkaz můžete provést v době kompilace (časné vazby) nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="192a9-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="192a9-105">Kompilace odkaz nastane, pokud kompilátoru určujete, že vaše sestavení explicitně odkazuje na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="192a9-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="192a9-106">Při použití odkazující na kompilaci kompilátor automaticky získá veřejný klíč cílové sestavení se silným názvem a umístí jej v odkazu na sestavení kompiluje sestavení.</span><span class="sxs-lookup"><span data-stu-id="192a9-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="192a9-107">Sestavení se silným názvem lze použít pouze typy z jiných sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="192a9-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="192a9-108">V opačném případě by dojít k ohrožení zabezpečení sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="192a9-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="192a9-109">Chcete-li kompilaci odkaz na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="192a9-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="192a9-110">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="192a9-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="192a9-111">\<*příkaz kompilátoru*> **/reference:**\<*název sestavení*></span><span class="sxs-lookup"><span data-stu-id="192a9-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="192a9-112">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk používáte, a *název sestavení* je název sestavení se silným názvem, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="192a9-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="192a9-113">Můžete také použít jiné možnosti kompilátoru, jako **/t:library** volba pro vytvoření sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="192a9-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="192a9-114">Následující příklad vytvoří sestavení nazvané `myAssembly.dll` , která odkazuje na sestavení se silným názvem se nazývá `myLibAssembly.dll` z modulu kódu volá `myAssembly.cs`.</span><span class="sxs-lookup"><span data-stu-id="192a9-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="192a9-115">Chcete-li za běhu odkaz na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="192a9-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="192a9-116">Když nastavíte za běhu odkaz na sestavení se silným názvem (například pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metoda), musíte použít zobrazovaný název odkazovaného sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="192a9-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="192a9-117">Název zobrazení syntaxe vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="192a9-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="192a9-118">\<*název sestavení*>**,** \< *číslo verze*>**,** \< *jazykovou verzi*  > **,** \< *token veřejného klíče*></span><span class="sxs-lookup"><span data-stu-id="192a9-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="192a9-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="192a9-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="192a9-120">V tomto příkladu `PublicKeyToken` je šestnáctkovém formátu token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="192a9-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="192a9-121">Pokud není žádná hodnota jazykové verze, použít `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="192a9-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="192a9-122">Následující příklad kódu ukazuje, jak pomocí těchto informací s <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="192a9-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="192a9-123">Můžete vytisknout šestnáctkovém formátu veřejný klíč a token veřejného klíče pro konkrétní sestavení pomocí následujících [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="192a9-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="192a9-124">**sériové číslo - Tp \<**  *sestavení* **>**</span><span class="sxs-lookup"><span data-stu-id="192a9-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="192a9-125">Pokud máte soubor veřejného klíče, můžete použít následující příkaz místo (Všimněte si rozdílů v případě na tuto možnost příkazového řádku):</span><span class="sxs-lookup"><span data-stu-id="192a9-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="192a9-126">**sériové číslo - tp \<**  *souboru veřejného klíče* **>**</span><span class="sxs-lookup"><span data-stu-id="192a9-126">**sn -tp \<** *public key file* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192a9-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="192a9-127">See also</span></span>

- [<span data-ttu-id="192a9-128">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="192a9-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
