---
title: 'Postupy: sdílení sestavení s jinými aplikacemi (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: a5b20061c759fd914193f24aa123317f13d31dce
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638393"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="39df8-102">Postupy: sdílení sestavení s jinými aplikacemi (C#)</span><span class="sxs-lookup"><span data-stu-id="39df8-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="39df8-103">Sestavení mohou být privátní nebo sdílené: ve výchozím nastavení, většina jednoduché programy obsahovat soukromé sestavení vzhledem k tomu, že nejsou určena pro použití jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="39df8-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="39df8-104">Pokud chcete sdílení sestavení s jinými aplikacemi, musí být umístěn v [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="39df8-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="39df8-105">Sdílení sestavení</span><span class="sxs-lookup"><span data-stu-id="39df8-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="39df8-106">Vytvoření vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="39df8-106">Create your assembly.</span></span> <span data-ttu-id="39df8-107">Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="39df8-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="39df8-108">K sestavení přiřadíte silný název.</span><span class="sxs-lookup"><span data-stu-id="39df8-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="39df8-109">Další informace najdete v tématu [postupy: podepsání sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="39df8-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="39df8-110">Informace o verzi přiřadíte k sestavení.</span><span class="sxs-lookup"><span data-stu-id="39df8-110">Assign version information to your assembly.</span></span> <span data-ttu-id="39df8-111">Další informace najdete v tématu [Správa verzí sestavení](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="39df8-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="39df8-112">Přidáte sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="39df8-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="39df8-113">Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="39df8-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="39df8-114">Přístup k typům obsaženy v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="39df8-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="39df8-115">Další informace najdete v tématu [postupy: odkazování na sestavení se silným názvem](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="39df8-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39df8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="39df8-116">See Also</span></span>

- [<span data-ttu-id="39df8-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="39df8-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="39df8-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="39df8-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
