---
title: 'Postupy: Sdílení sestavení s jinými aplikacemi (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: d0e1dafc700b55a63342331b3280337d2c93cbd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631825"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>Postupy: Sdílení sestavení s jinými aplikacemi (Visual Basic)
Sestavení mohou být privátní nebo sdílené: ve výchozím nastavení, většina jednoduché programy obsahovat soukromé sestavení vzhledem k tomu, že nejsou určena pro použití jiné aplikace.  
  
 Pokud chcete sdílení sestavení s jinými aplikacemi, musí být umístěn v [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Sdílení sestavení  
  
1.  Vytvoření vašeho sestavení. Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).  
  
2.  K sestavení přiřadíte silný název. Další informace najdete v tématu [jak: Podepsání sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Informace o verzi přiřadíte k sestavení. Další informace najdete v tématu [Správa verzí sestavení](../../../../framework/app-domains/assembly-versioning.md).  
  
4.  Přidáte sestavení do globální mezipaměti sestavení. Další informace najdete v tématu [jak: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Přístup k typům obsaženy v sestavení z jiných aplikací. Další informace najdete v tématu [jak: Odkazování na sestavení se silným názvem](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Viz také:

- [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)
