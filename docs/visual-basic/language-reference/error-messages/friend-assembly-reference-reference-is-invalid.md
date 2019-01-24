---
title: Odkaz na sestavení typu Friend &lt;odkaz&gt; je neplatný
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: cdedcc18aa82f6efd8c52cdca5d915d7d78e269f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611927"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="1dbee-102">Odkaz na sestavení typu Friend &lt;odkaz&gt; je neplatný</span><span class="sxs-lookup"><span data-stu-id="1dbee-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="1dbee-103">Odkaz na sestavení typu Friend \<odkaz > je neplatný.</span><span class="sxs-lookup"><span data-stu-id="1dbee-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="1dbee-104">Podepsaná sestavení silným názvem je nutné zadat veřejný klíč v jejich deklaracích InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="1dbee-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="1dbee-105">Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktor atributu identifikuje sestavení se silným názvem, ale nezahrnuje `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="1dbee-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="1dbee-106">**ID chyby:** BC31535</span><span class="sxs-lookup"><span data-stu-id="1dbee-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1dbee-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1dbee-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="1dbee-108">Určení veřejný klíč pro sestavení typu friend se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="1dbee-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="1dbee-109">Zahrnovat veřejný klíč jako součást názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktor atributu pomocí `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="1dbee-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbee-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dbee-110">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="1dbee-111">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="1dbee-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


