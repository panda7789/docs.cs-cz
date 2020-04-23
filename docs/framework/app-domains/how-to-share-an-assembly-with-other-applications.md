---
title: 'Postupy: sdílení sestavení s jinými aplikacemi'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644293"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Postupy: sdílení sestavení s jinými aplikacemi
Sestavení mohou být soukromá nebo sdílená: ve výchozím nastavení se většina jednoduchých programů skládá z privátního sestavení, protože nejsou určeny pro použití jinými aplikacemi.  

Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěn v [globální mezipaměti sestavení (GAC)](gac.md).  
  
Sdílení sestavení:
  
1. Vytvořte sestavení. Další informace naleznete v tématu [Create Assemblies](../../standard/assembly/create.md).  
  
2. Přiřaďte sestavení silný název. Další informace najdete v tématu [Postup: podepsání sestavení silným názvem](../../standard/assembly/sign-strong-name.md).  
  
3. Přiřaďte k sestavení informace o verzi. Další informace naleznete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).  
  
4. Přidejte sestavení do globální mezipaměti sestavení (GAC). Další informace naleznete v tématu [Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC](install-assembly-into-gac.md)).  
  
5. Přístup k typům obsaženým v sestavení z jiných aplikací. Další informace naleznete v tématu [Postupy: odkazování na sestavení se silným názvem](../../standard/assembly/reference-strong-named.md).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../../../api/index.md)
- [Koncepty programování (Visual Basic)](../../../api/index.md)
- [Programování se sestaveními](../../standard/assembly/index.md)
