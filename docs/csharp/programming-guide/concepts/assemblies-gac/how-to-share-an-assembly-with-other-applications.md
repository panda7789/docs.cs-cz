---
title: 'Postupy: sdílení sestavení s jinými aplikacemi (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 413eb5e021c782db05abd454ebfa4e7cb1a1abcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512905"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Postupy: sdílení sestavení s jinými aplikacemi (C#)
Sestavení mohou být privátní nebo sdílené: ve výchozím nastavení, většina jednoduché programy obsahovat soukromé sestavení vzhledem k tomu, že nejsou určena pro použití jiné aplikace.  
  
 Pokud chcete sdílení sestavení s jinými aplikacemi, musí být umístěn v [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Sdílení sestavení  
  
1.  Vytvoření vašeho sestavení. Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).  
  
2.  K sestavení přiřadíte silný název. Další informace najdete v tématu [postupy: podepsání sestavení silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Informace o verzi přiřadíte k sestavení. Další informace najdete v tématu [Správa verzí sestavení](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4.  Přidáte sestavení do globální mezipaměti sestavení. Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Přístup k typům obsaženy v sestavení z jiných aplikací. Další informace najdete v tématu [postupy: odkazování na sestavení se silným názvem](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)
