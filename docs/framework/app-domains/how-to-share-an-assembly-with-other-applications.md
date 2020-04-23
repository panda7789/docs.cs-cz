---
title: 'Postupy: sdílení sestavení s jinými aplikacemi'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644293"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="8e860-102">Postupy: sdílení sestavení s jinými aplikacemi</span><span class="sxs-lookup"><span data-stu-id="8e860-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="8e860-103">Sestavení mohou být soukromá nebo sdílená: ve výchozím nastavení se většina jednoduchých programů skládá z privátního sestavení, protože nejsou určeny pro použití jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="8e860-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="8e860-104">Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěn v [globální mezipaměti sestavení (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="8e860-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="8e860-105">Sdílení sestavení:</span><span class="sxs-lookup"><span data-stu-id="8e860-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="8e860-106">Vytvořte sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e860-106">Create your assembly.</span></span> <span data-ttu-id="8e860-107">Další informace naleznete v tématu [Create Assemblies](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="8e860-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="8e860-108">Přiřaďte sestavení silný název.</span><span class="sxs-lookup"><span data-stu-id="8e860-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="8e860-109">Další informace najdete v tématu [Postup: podepsání sestavení silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="8e860-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="8e860-110">Přiřaďte k sestavení informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="8e860-110">Assign version information to your assembly.</span></span> <span data-ttu-id="8e860-111">Další informace naleznete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="8e860-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="8e860-112">Přidejte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="8e860-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="8e860-113">Další informace naleznete v tématu [Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC](install-assembly-into-gac.md)).</span><span class="sxs-lookup"><span data-stu-id="8e860-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="8e860-114">Přístup k typům obsaženým v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="8e860-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="8e860-115">Další informace naleznete v tématu [Postupy: odkazování na sestavení se silným názvem](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="8e860-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e860-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e860-116">See also</span></span>

- [<span data-ttu-id="8e860-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8e860-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="8e860-118">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e860-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="8e860-119">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="8e860-119">Program with assemblies</span></span>](../../standard/assembly/index.md)
