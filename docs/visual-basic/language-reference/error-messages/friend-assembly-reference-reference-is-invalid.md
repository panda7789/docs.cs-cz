---
title: "Odkaz sestavení Friend &lt;odkaz&gt; je neplatný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="adf93-102">Odkaz sestavení Friend &lt;odkaz&gt; je neplatný</span><span class="sxs-lookup"><span data-stu-id="adf93-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="adf93-103">Odkaz sestavení Friend \<reference > je neplatný.</span><span class="sxs-lookup"><span data-stu-id="adf93-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="adf93-104">Podepsaná sestavení silného názvu do svých prohlášeních InternalsVisibleTo nutné zadat veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="adf93-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="adf93-105">Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu identifikuje sestavení se silným názvem, ale neobsahuje `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="adf93-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="adf93-106">**ID chyby:** BC31535</span><span class="sxs-lookup"><span data-stu-id="adf93-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="adf93-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="adf93-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="adf93-108">Určení veřejný klíč pro sestavení silným názvem friend.</span><span class="sxs-lookup"><span data-stu-id="adf93-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="adf93-109">Zadejte veřejný klíč jako část názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu pomocí `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="adf93-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf93-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="adf93-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="adf93-111">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="adf93-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

