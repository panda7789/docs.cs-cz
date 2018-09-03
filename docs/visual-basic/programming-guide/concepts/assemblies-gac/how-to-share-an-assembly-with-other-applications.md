---
title: 'Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: a7f6b49e8389108528c44d7464a2e68149dfa940
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466473"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="a8512-102">Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8512-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="a8512-103">Sestavení mohou být privátní nebo sdílené: ve výchozím nastavení, většina jednoduché programy obsahovat soukromé sestavení vzhledem k tomu, že nejsou určena pro použití jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8512-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="a8512-104">Pokud chcete sdílení sestavení s jinými aplikacemi, musí být umístěn v [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="a8512-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="a8512-105">Sdílení sestavení</span><span class="sxs-lookup"><span data-stu-id="a8512-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="a8512-106">Vytvoření vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8512-106">Create your assembly.</span></span> <span data-ttu-id="a8512-107">Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a8512-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="a8512-108">K sestavení přiřadíte silný název.</span><span class="sxs-lookup"><span data-stu-id="a8512-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="a8512-109">Další informace najdete v tématu [postupy: podepsání sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a8512-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="a8512-110">Informace o verzi přiřadíte k sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8512-110">Assign version information to your assembly.</span></span> <span data-ttu-id="a8512-111">Další informace najdete v tématu [Správa verzí sestavení](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="a8512-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="a8512-112">Přidáte sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8512-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="a8512-113">Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="a8512-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="a8512-114">Přístup k typům obsaženy v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="a8512-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="a8512-115">Další informace najdete v tématu [postupy: odkazování na sestavení se silným názvem](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="a8512-115">For more information, see [How to: Reference a Strong-Named Assembly](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8512-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8512-116">See Also</span></span>  
 <span data-ttu-id="a8512-117">[Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md) [sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="a8512-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="a8512-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="a8512-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
