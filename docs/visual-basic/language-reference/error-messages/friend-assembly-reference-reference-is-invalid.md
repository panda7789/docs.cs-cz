---
title: Odkaz na sestavení typu <reference> Friend není platný.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 796c16e912283d86496a4ccbd3b675ac1433f02d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356400"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="e3c13-102">Odkaz na sestavení typu Friend \<odkaz > je neplatný</span><span class="sxs-lookup"><span data-stu-id="e3c13-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="e3c13-103">Odkaz na sestavení typu Friend \<odkaz > je neplatný.</span><span class="sxs-lookup"><span data-stu-id="e3c13-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="e3c13-104">Podepsaná sestavení silným názvem je nutné zadat veřejný klíč v jejich deklaracích InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="e3c13-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="e3c13-105">Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktor atributu identifikuje sestavení se silným názvem, ale nezahrnuje `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="e3c13-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="e3c13-106">**ID chyby:** BC31535</span><span class="sxs-lookup"><span data-stu-id="e3c13-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3c13-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e3c13-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="e3c13-108">Určení veřejný klíč pro sestavení typu friend se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e3c13-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="e3c13-109">Zahrnovat veřejný klíč jako součást názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktor atributu pomocí `PublicKey` atribut.</span><span class="sxs-lookup"><span data-stu-id="e3c13-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c13-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3c13-110">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="e3c13-111">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="e3c13-111">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)


