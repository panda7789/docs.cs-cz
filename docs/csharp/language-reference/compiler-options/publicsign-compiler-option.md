---
title: -publicsign (C# Možnosti kompilátoru)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662527"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="8f7b4-102">-publicsign (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="8f7b4-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="8f7b4-103">Tato možnost způsobí, že kompilátor použít veřejný klíč, ale ve skutečnosti nepodepisuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="8f7b4-104">Možnost **-publicsign** také nastaví bit v sestavení, který říká, že soubor je skutečně podepsán.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f7b4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f7b4-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="8f7b4-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8f7b4-106">Arguments</span></span>

<span data-ttu-id="8f7b4-107">Žádné.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f7b4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f7b4-108">Remarks</span></span>

<span data-ttu-id="8f7b4-109">Možnost **-publicsign** vyžaduje použití [-keyfile](keyfile-compiler-option.md) nebo [-keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="8f7b4-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="8f7b4-110">Možnosti **keyfile** nebo **keycontainer** určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="8f7b4-111">Možnosti **-publicsign** a **-delaysign** se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="8f7b4-112">Někdy se nazývá "falešné znamení" nebo "znak OSS", veřejné podepisování zahrnuje veřejný klíč ve výstupním sestavení a nastaví příznak "podepsáno", ale ve skutečnosti nepodepisuje sestavení pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="8f7b4-113">To je užitečné pro projekty s otevřeným zdrojovým kódem, kde uživatelé chtějí vytvářet sestavení, která jsou kompatibilní s vydanými "plně podepsanými" sestaveními, ale nemají přístup k soukromému klíči používanému k podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="8f7b4-114">Vzhledem k tomu, že téměř žádní spotřebitelé skutečně potřebují zkontrolovat, zda je sestavení plně podepsáno, jsou tato veřejně vytvořená sestavení použitelná téměř ve všech scénářích, kde by bylo použito plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8f7b4-115">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8f7b4-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="8f7b4-116">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="8f7b4-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="8f7b4-117">Upravte pouze vlastnost **znaménko Zpoždění.**</span><span class="sxs-lookup"><span data-stu-id="8f7b4-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f7b4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f7b4-118">See also</span></span>

- [<span data-ttu-id="8f7b4-119">C# Compiler -delaysign, volba</span><span class="sxs-lookup"><span data-stu-id="8f7b4-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="8f7b4-120">C# Kompilátor -keyfile, volba</span><span class="sxs-lookup"><span data-stu-id="8f7b4-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="8f7b4-121">C# Kompilátor -keycontainer, možnost</span><span class="sxs-lookup"><span data-stu-id="8f7b4-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="8f7b4-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8f7b4-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="8f7b4-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="8f7b4-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
