---
title: "Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 491791ba9b6f0cf6da86a160eddf8e78109b11c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="58954-102">Postupy: sdílení sestavení s jinými aplikacemi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58954-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="58954-103">Sestavení může být privátní nebo sdílené: ve výchozím nastavení, většiny programů jednoduché skládat z privátní sestavení, protože není určen pro použití jinými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="58954-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="58954-104">Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěny v [globální mezipaměti sestavení](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="58954-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="58954-105">Sdílení sestavení</span><span class="sxs-lookup"><span data-stu-id="58954-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="58954-106">Vytvoření vašeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="58954-106">Create your assembly.</span></span> <span data-ttu-id="58954-107">Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="58954-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="58954-108">Přiřadíte vaše sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="58954-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="58954-109">Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="58954-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="58954-110">Informace o verzi přiřadíte vaše sestavení.</span><span class="sxs-lookup"><span data-stu-id="58954-110">Assign version information to your assembly.</span></span> <span data-ttu-id="58954-111">Další informace najdete v tématu [Správa verzí sestavení](https://msdn.microsoft.com/library/51ket42z).</span><span class="sxs-lookup"><span data-stu-id="58954-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="58954-112">Přidejte vaše sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="58954-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="58954-113">Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="58954-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="58954-114">Přístup k typům obsažený v sestavení z jiných aplikací.</span><span class="sxs-lookup"><span data-stu-id="58954-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="58954-115">Další informace najdete v tématu [postupy: odkazování sestavení silným názvem](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="58954-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58954-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="58954-116">See Also</span></span>  
 <span data-ttu-id="58954-117">[Programování konceptů](../../../../visual-basic/programming-guide/concepts/index.md) [sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="58954-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="58954-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="58954-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
