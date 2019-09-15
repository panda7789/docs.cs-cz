---
title: 'Postupy: Sdílení sestavení s jinými aplikacemi'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972947"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Postupy: Sdílení sestavení s jinými aplikacemi
Sestavení mohou být soukromá nebo sdílená: ve výchozím nastavení se většina jednoduchých programů skládá z privátního sestavení, protože nejsou určeny pro použití jinými aplikacemi.  

Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěn v [globální mezipaměti sestavení (GAC)](gac.md).  
  
Sdílení sestavení:
  
1. Vytvořte sestavení. Další informace naleznete v tématu [Create Assemblies](../../standard/assembly/create.md).  
  
2. Přiřaďte sestavení silný název. Další informace najdete v tématu [jak: Podepište sestavení silným názvem](../../standard/assembly/sign-strong-name.md).  
  
3. Přiřaďte k sestavení informace o verzi. Další informace naleznete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).  
  
4. Přidejte sestavení do globální mezipaměti sestavení (GAC). Další informace najdete v tématu [jak: Nainstalujte sestavení do globální mezipaměti](install-assembly-into-gac.md)sestavení (GAC).  
  
5. Přístup k typům obsaženým v sestavení z jiných aplikací. Další informace najdete v tématu [jak: Odkazování na sestavení](../../standard/assembly/reference-strong-named.md)se silným názvem.  
  
## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../../../api/index.md)
- [Koncepty programování (Visual Basic)](../../../api/index.md)
- [Program se sestaveními](../../standard/assembly/program.md)
