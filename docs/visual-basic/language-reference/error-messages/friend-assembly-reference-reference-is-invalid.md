---
title: Odkaz na sestavení typu <reference> Friend není platný.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972393"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>\<Referenční > odkazu na sestavení typu Friend je neplatný.
> Odkazu na \<odkaz na sestavení typu Friend je neplatný. Sestavení podepsaná silným názvem musí v deklaracích InternalsVisibleTo určovat veřejný klíč.  
  
 Název sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu identifikuje sestavení se silným názvem, ale `PublicKey` nezahrnuje atribut.  
  
 **ID chyby:** BC31535  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Určete veřejný klíč pro sestavení typu Friend se silným názvem. Zahrňte veřejný klíč jako součást názvu sestavení předaného <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu `PublicKey` pomocí atributu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.AssemblyName>
- [Přátelská sestavení](../../../standard/assembly/friend.md)
