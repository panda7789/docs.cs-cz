---
title: "Odkaz sestavení Friend &lt;odkaz&gt; je neplatný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Odkaz sestavení Friend &lt;odkaz&gt; je neplatný
Odkaz sestavení Friend \<reference > je neplatný. Podepsaná sestavení silného názvu do svých prohlášeních InternalsVisibleTo nutné zadat veřejný klíč.  
  
 Předaný název sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu identifikuje sestavení se silným názvem, ale neobsahuje `PublicKey` atribut.  
  
 **ID chyby:** BC31535  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určení veřejný klíč pro sestavení silným názvem friend. Zadejte veřejný klíč jako část názvu sestavení předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> konstruktoru atributu pomocí `PublicKey` atribut.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.AssemblyName>  
 [Přátelská sestavení](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [Postupy: vytváření podepsaných přátelských sestavení](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
