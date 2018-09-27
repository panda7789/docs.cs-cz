---
title: 'Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 3d29a3558a64c02fc8c59035f2fee5c64c4a776f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235241"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="db6af-102">Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6af-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="db6af-103">Sestavení mohou být privátní nebo sdílené: ve výchozím nastavení, většina jednoduché programy obsahovat soukromé sestavení vzhledem k tomu, že nejsou určena pro použití jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="db6af-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="db6af-104">Pokud chcete sdílení sestavení s jinými aplikacemi, musí být umístěn v [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="db6af-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="db6af-105">Sdílení sestavení</span><span class="sxs-lookup"><span data-stu-id="db6af-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="db6af-106">Vytvoření vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="db6af-106">Create your assembly.</span></span> <span data-ttu-id="db6af-107">Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="db6af-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="db6af-108">K sestavení přiřadíte silný název.</span><span class="sxs-lookup"><span data-stu-id="db6af-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="db6af-109">Další informace najdete v tématu [postupy: podepsání sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="db6af-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="db6af-110">Informace o verzi přiřadíte k sestavení.</span><span class="sxs-lookup"><span data-stu-id="db6af-110">Assign version information to your assembly.</span></span> <span data-ttu-id="db6af-111">Další informace najdete v tématu [Správa verzí sestavení](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="db6af-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="db6af-112">Přidáte sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="db6af-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="db6af-113">Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="db6af-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="db6af-114">Přístup k typům obsaženy v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="db6af-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="db6af-115">Další informace najdete v tématu [postupy: odkazování na sestavení se silným názvem](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="db6af-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6af-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db6af-116">See also</span></span>

- [<span data-ttu-id="db6af-117">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="db6af-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="db6af-118">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6af-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="db6af-119">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="db6af-119">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
