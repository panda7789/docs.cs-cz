---
title: 'Postupy: Sdílení sestavení s jinými aplikacemi (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595740"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Postupy: Sdílení sestavení s jinými aplikacemi (C#)
Sestavení mohou být soukromá nebo sdílená: ve výchozím nastavení se většina jednoduchých programů skládá z privátního sestavení, protože nejsou určeny pro použití jinými aplikacemi.  
  
 Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěn v [globální mezipaměti sestavení](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Sdílení sestavení  
  
1. Vytvořte sestavení. Další informace naleznete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).  
  
2. Přiřaďte sestavení silný název. Další informace najdete v tématu [jak: Podepište sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Přiřaďte k sestavení informace o verzi. Další informace naleznete v tématu [Správa verzí sestavení](../../../../framework/app-domains/assembly-versioning.md).  
  
4. Přidejte sestavení do globální mezipaměti sestavení (GAC). Další informace najdete v tématu [jak: Nainstalujte sestavení do globální mezipaměti](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)sestavení (GAC).  
  
5. Přístup k typům obsaženým v sestavení z jiných aplikací. Další informace najdete v tématu [jak: Odkazování na sestavení](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)se silným názvem.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../index.md)
- [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)
