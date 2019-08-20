---
title: 'Postupy: Sdílení sestavení s jinými aplikacemi (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595740"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="610aa-102">Postupy: Sdílení sestavení s jinými aplikacemi (C#)</span><span class="sxs-lookup"><span data-stu-id="610aa-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="610aa-103">Sestavení mohou být soukromá nebo sdílená: ve výchozím nastavení se většina jednoduchých programů skládá z privátního sestavení, protože nejsou určeny pro použití jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="610aa-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="610aa-104">Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěn v [globální mezipaměti sestavení](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="610aa-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="610aa-105">Sdílení sestavení</span><span class="sxs-lookup"><span data-stu-id="610aa-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="610aa-106">Vytvořte sestavení.</span><span class="sxs-lookup"><span data-stu-id="610aa-106">Create your assembly.</span></span> <span data-ttu-id="610aa-107">Další informace naleznete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="610aa-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="610aa-108">Přiřaďte sestavení silný název.</span><span class="sxs-lookup"><span data-stu-id="610aa-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="610aa-109">Další informace najdete v tématu [jak: Podepište sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="610aa-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="610aa-110">Přiřaďte k sestavení informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="610aa-110">Assign version information to your assembly.</span></span> <span data-ttu-id="610aa-111">Další informace naleznete v tématu [Správa verzí sestavení](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="610aa-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="610aa-112">Přidejte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="610aa-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="610aa-113">Další informace najdete v tématu [jak: Nainstalujte sestavení do globální mezipaměti](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="610aa-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="610aa-114">Přístup k typům obsaženým v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="610aa-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="610aa-115">Další informace najdete v tématu [jak: Odkazování na sestavení](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="610aa-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610aa-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="610aa-116">See also</span></span>

- [<span data-ttu-id="610aa-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="610aa-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="610aa-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="610aa-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
