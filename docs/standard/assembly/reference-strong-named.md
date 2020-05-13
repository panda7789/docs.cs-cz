---
title: 'Postupy: odkazování na sestavení se silným názvem'
description: V tomto článku se dozvíte, jak odkazovat na typy nebo prostředky v sestavení .NET se silným názvem, a to buď v době kompilace, nebo v modulu runtime.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: e42c1b461da16d7000605b9b9321138bbfebd307
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379865"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="2a382-103">Postupy: odkazování na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="2a382-103">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="2a382-104">Proces pro odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní.</span><span class="sxs-lookup"><span data-stu-id="2a382-104">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="2a382-105">Odkaz lze vytvořit buď v době kompilace (počáteční vazba), nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2a382-105">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="2a382-106">K referenci v době kompilace dojde, když označíte kompilátor, že sestavení, které má být zkompilováno, explicitně odkazuje na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a382-106">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="2a382-107">Použijete-li referenční informace při kompilaci, kompilátor automaticky získá veřejný klíč cílového sestavení se silným názvem a umístí jej do odkazu na sestavení zkompilovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a382-107">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2a382-108">Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="2a382-108">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="2a382-109">V opačném případě by došlo k ohrožení zabezpečení sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="2a382-109">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="2a382-110">Vytvoření odkazu na sestavení v čase kompilace na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="2a382-110">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="2a382-111">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2a382-111">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="2a382-112">\<*příkaz kompilátoru* >  **/Reference:** \< *název sestavení*></span><span class="sxs-lookup"><span data-stu-id="2a382-112">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="2a382-113">V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk, který používáte, a *názvem sestavení* je název odkazovaného sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="2a382-113">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="2a382-114">Můžete také použít další možnosti kompilátoru, jako je například možnost **/t: Library** pro vytvoření sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="2a382-114">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="2a382-115">Následující příklad vytvoří sestavení s názvem *MyAssembly. dll* , které odkazuje na sestavení se silným názvem s názvem *myLibAssembly. dll* z modulu kódu s názvem *MyAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="2a382-115">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="2a382-116">Vytvoření reference za běhu na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="2a382-116">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="2a382-117">Když vytvoříte odkaz na sestavení se silným názvem, například pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metody nebo, musíte použít zobrazovaný název odkazovaného sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="2a382-117">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="2a382-118">Syntaxe zobrazovaného názvu je následující:</span><span class="sxs-lookup"><span data-stu-id="2a382-118">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="2a382-119">\<*název sestavení* > **,** \< *číslo verze* > **,** \< *jazyková verze* > **,** \< *token veřejného klíče*></span><span class="sxs-lookup"><span data-stu-id="2a382-119">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="2a382-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2a382-120">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="2a382-121">V tomto příkladu `PublicKeyToken` je hexadecimální forma tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="2a382-121">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="2a382-122">Pokud není k dispozici žádná hodnota jazykové verze, použijte `Culture=neutral` .</span><span class="sxs-lookup"><span data-stu-id="2a382-122">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="2a382-123">Následující příklad kódu ukazuje, jak použít tyto informace s <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="2a382-123">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="2a382-124">Můžete vytisknout hexadecimální formát veřejného klíče a tokenu veřejného klíče pro konkrétní sestavení pomocí následujícího příkazu [silného názvu (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="2a382-124">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="2a382-125">\**sn-TP \< \*\* *sestavení\*\*\*>**</span><span class="sxs-lookup"><span data-stu-id="2a382-125">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="2a382-126">Pokud máte soubor s veřejným klíčem, můžete místo toho použít následující příkaz (Poznamenejte si rozdíl v případě použití možnosti příkazového řádku):</span><span class="sxs-lookup"><span data-stu-id="2a382-126">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="2a382-127">\**sn-TP \< \*\* *soubor veřejného klíče\*\*\*>**</span><span class="sxs-lookup"><span data-stu-id="2a382-127">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="2a382-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a382-128">See also</span></span>

- [<span data-ttu-id="2a382-129">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="2a382-129">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
