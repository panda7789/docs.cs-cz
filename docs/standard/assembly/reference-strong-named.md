---
title: 'Postupy: odkazování na sestavení se silným názvem'
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
ms.openlocfilehash: 427550e1fbeb38cefbb4afe97d80e198ac2d6cb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127637"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="96f26-102">Postupy: odkazování na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="96f26-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="96f26-103">Proces pro odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní.</span><span class="sxs-lookup"><span data-stu-id="96f26-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="96f26-104">Odkaz lze vytvořit buď v době kompilace (počáteční vazba), nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="96f26-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="96f26-105">K referenci v době kompilace dojde, když označíte kompilátor, že sestavení, které má být zkompilováno, explicitně odkazuje na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="96f26-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="96f26-106">Použijete-li referenční informace při kompilaci, kompilátor automaticky získá veřejný klíč cílového sestavení se silným názvem a umístí jej do odkazu na sestavení zkompilovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="96f26-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="96f26-107">Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="96f26-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="96f26-108">V opačném případě by došlo k ohrožení zabezpečení sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="96f26-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="96f26-109">Vytvoření odkazu na sestavení v čase kompilace na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="96f26-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="96f26-110">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="96f26-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="96f26-111">\<*příkaz kompilátoru*>  **/Reference:** \<*název sestavení*></span><span class="sxs-lookup"><span data-stu-id="96f26-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="96f26-112">V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk, který používáte, a *názvem sestavení* je název odkazovaného sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="96f26-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="96f26-113">Můžete také použít další možnosti kompilátoru, jako je například možnost **/t: Library** pro vytvoření sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="96f26-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="96f26-114">Následující příklad vytvoří sestavení s názvem *MyAssembly. dll* , které odkazuje na sestavení se silným názvem s názvem *myLibAssembly. dll* z modulu kódu s názvem *MyAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="96f26-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="96f26-115">Vytvoření reference za běhu na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="96f26-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="96f26-116">Když vytvoříte odkaz na sestavení se silným názvem, například pomocí metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>, je nutné použít zobrazovaný název odkazovaného sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="96f26-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="96f26-117">Syntaxe zobrazovaného názvu je následující:</span><span class="sxs-lookup"><span data-stu-id="96f26-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="96f26-118">\<*název sestavení*> **,** \<*číslo verze*> **,** \<*culture*> **,** \<*tokenu veřejného klíče*></span><span class="sxs-lookup"><span data-stu-id="96f26-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="96f26-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="96f26-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

<span data-ttu-id="96f26-120">V tomto příkladu je `PublicKeyToken` hexadecimální formou tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="96f26-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="96f26-121">Pokud není k dispozici žádná hodnota jazykové verze, použijte `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="96f26-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="96f26-122">Následující příklad kódu ukazuje, jak použít tyto informace s metodou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96f26-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

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

<span data-ttu-id="96f26-123">Můžete vytisknout hexadecimální formát veřejného klíče a tokenu veřejného klíče pro konkrétní sestavení pomocí následujícího příkazu [silného názvu (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="96f26-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="96f26-124">\<*sestavení* **>** **sn-TP**</span><span class="sxs-lookup"><span data-stu-id="96f26-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="96f26-125">Pokud máte soubor s veřejným klíčem, můžete místo toho použít následující příkaz (Poznamenejte si rozdíl v případě použití možnosti příkazového řádku):</span><span class="sxs-lookup"><span data-stu-id="96f26-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="96f26-126">**sn-tp \<** *soubor veřejného klíče* **>**</span><span class="sxs-lookup"><span data-stu-id="96f26-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="96f26-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96f26-127">See also</span></span>

- [<span data-ttu-id="96f26-128">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="96f26-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
