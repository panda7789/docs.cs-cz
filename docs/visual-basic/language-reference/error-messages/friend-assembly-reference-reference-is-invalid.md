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
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Odkaz sestavení Friend &lt;odkaz&gt; je neplatný
Odkaz sestavení Friend \<reference > je neplatný. Podepsaná sestavení silného názvu do svých prohlášeních InternalsVisibleTo nutné zadat veřejný klíč.  
  
 Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu identifikuje sestavení se silným názvem, ale neobsahuje `PublicKey` atribut.  
  
 **ID chyby:** BC31535  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určení veřejný klíč pro sestavení silným názvem friend. Zadejte veřejný klíč jako část názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu pomocí `PublicKey` atribut.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.AssemblyName>  
 [Přátelská sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

