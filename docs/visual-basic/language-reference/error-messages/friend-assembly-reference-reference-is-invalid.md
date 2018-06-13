---
title: Odkaz sestavení Friend &lt;odkaz&gt; je neplatný
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587368"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="88305-102">Odkaz sestavení Friend &lt;odkaz&gt; je neplatný</span><span class="sxs-lookup"><span data-stu-id="88305-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="88305-103">Odkaz sestavení Friend \<reference > je neplatný.</span><span class="sxs-lookup"><span data-stu-id="88305-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="88305-104">Podepsaná sestavení silného názvu do svých prohlášeních InternalsVisibleTo nutné zadat veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="88305-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="88305-105">Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu identifikuje sestavení se silným názvem, ale neobsahuje `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="88305-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="88305-106">**ID chyby:** BC31535</span><span class="sxs-lookup"><span data-stu-id="88305-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88305-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="88305-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="88305-108">Určení veřejný klíč pro sestavení silným názvem friend.</span><span class="sxs-lookup"><span data-stu-id="88305-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="88305-109">Zadejte veřejný klíč jako část názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu pomocí `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="88305-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88305-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="88305-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="88305-111">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="88305-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

