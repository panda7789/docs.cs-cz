---
title: 'Postupy: Sdílení sestavení s jinými aplikacemi'
description: Viz jak sdílet sestavení s jinými aplikacemi v rozhraní .NET. Sestavení mohou být soukromá (výchozí) nebo sdílená. Chcete-li sdílet sestavení, umístěte ho do globální mezipaměti sestavení (GAC).
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 9cef25059968875f17ce5dc77b04c44a2f3945f6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104644"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="a496d-105">Postupy: Sdílení sestavení s jinými aplikacemi</span><span class="sxs-lookup"><span data-stu-id="a496d-105">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="a496d-106">Sestavení mohou být soukromá nebo sdílená: ve výchozím nastavení se většina jednoduchých programů skládá z privátního sestavení, protože nejsou určeny pro použití jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="a496d-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="a496d-107">Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěn v [globální mezipaměti sestavení (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="a496d-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="a496d-108">Sdílení sestavení:</span><span class="sxs-lookup"><span data-stu-id="a496d-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="a496d-109">Vytvořte sestavení.</span><span class="sxs-lookup"><span data-stu-id="a496d-109">Create your assembly.</span></span> <span data-ttu-id="a496d-110">Další informace naleznete v tématu [Create Assemblies](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="a496d-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="a496d-111">Přiřaďte sestavení silný název.</span><span class="sxs-lookup"><span data-stu-id="a496d-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="a496d-112">Další informace najdete v tématu [Postup: podepsání sestavení silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a496d-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="a496d-113">Přiřaďte k sestavení informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="a496d-113">Assign version information to your assembly.</span></span> <span data-ttu-id="a496d-114">Další informace naleznete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="a496d-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="a496d-115">Přidejte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="a496d-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="a496d-116">Další informace naleznete v tématu [Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC](install-assembly-into-gac.md)).</span><span class="sxs-lookup"><span data-stu-id="a496d-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="a496d-117">Přístup k typům obsaženým v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="a496d-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="a496d-118">Další informace naleznete v tématu [Postupy: odkazování na sestavení se silným názvem](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="a496d-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a496d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a496d-119">See also</span></span>

- [<span data-ttu-id="a496d-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a496d-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="a496d-121">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a496d-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="a496d-122">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="a496d-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
