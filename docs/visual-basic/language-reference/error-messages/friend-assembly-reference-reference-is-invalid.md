---
title: Odkaz na sestavení typu <reference> Friend není platný.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: ff2cdbebe13f6224209ef8da62600c99348c911b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286816"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Odkaz na sestavení typu Friend \<odkaz > je neplatný
Odkaz na sestavení typu Friend \<odkaz > je neplatný. Podepsaná sestavení silným názvem je nutné zadat veřejný klíč v jejich deklaracích InternalsVisibleTo.  
  
 Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktor atributu identifikuje sestavení se silným názvem, ale nezahrnuje `PublicKey` atribut.  
  
 **ID chyby:** BC31535  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určení veřejný klíč pro sestavení typu friend se silným názvem. Zahrnovat veřejný klíč jako součást názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktor atributu pomocí `PublicKey` atribut.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Reflection.AssemblyName>
- [Přátelská sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


