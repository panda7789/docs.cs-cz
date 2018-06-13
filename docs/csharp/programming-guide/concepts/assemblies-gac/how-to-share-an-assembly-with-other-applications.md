---
title: 'Postupy: sdílení sestavení s jinými aplikacemi (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: beadd6adb176c3fd4e6dde94d95194aea790a2fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324119"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Postupy: sdílení sestavení s jinými aplikacemi (C#)
Sestavení může být privátní nebo sdílené: ve výchozím nastavení, většiny programů jednoduché skládat z privátní sestavení, protože není určen pro použití jinými aplikacemi.  
  
 Aby bylo možné sdílet sestavení s jinými aplikacemi, musí být umístěny v [globální mezipaměti sestavení](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Sdílení sestavení  
  
1.  Vytvoření vašeho sestavení. Další informace najdete v tématu [vytváření sestavení](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Přiřadíte vaše sestavení silným názvem. Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Informace o verzi přiřadíte vaše sestavení. Další informace najdete v tématu [Správa verzí sestavení](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4.  Přidejte vaše sestavení do globální mezipaměti sestavení. Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Přístup k typům obsažený v sestavení z jiných aplikací. Další informace najdete v tématu [postupy: odkazování sestavení silným názvem](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Programování se sestaveními](../../../../framework/app-domains/programming-with-assemblies.md)
