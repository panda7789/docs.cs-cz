---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c42e351808281d90eafdb6e61a3f1736ef15c9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign"></a>/delaysign
Určuje, zda bude sestavení zcela nebo částečně podepsáno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Použití `/delaysign-` Pokud chcete plně podepsané sestavení. Použití `/delaysign+` Pokud chcete umístit veřejný klíč v sestavení a rezervy místa pro podepsané hash. Výchozí hodnota je `/delaysign-`.  
  
## <a name="remarks"></a>Poznámky  
 `/delaysign` Možnost nemá žádný vliv, pokud není použita s [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash s privátním klíčem. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Při sestavení zpoždění, které jsou podepsané, kompilátor nepodporuje výpočetní a uložení podpis ale rezervy místa v souboru, takže podpis lze přidat později.  
  
 Například pomocí `/delaysign+`, vývojáři v organizaci můžete distribuovat nepodepsané testovací verze sestavení, které testery můžete zaregistrovat s globální mezipaměti sestavení a použít. Po dokončení práce na sestavení může osoba odpovědná za soukromého klíče organizace plně podepsat sestavení. Tato takové soukromého klíče organizace chrání před zpřístupnění současně všechny vývojářům pracovat na sestavení.  
  
 V tématu [vytvoření a použití sestavení](https://msdn.microsoft.com/library/xwb8f617) Další informace o podepisování sestavení.  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Chcete-li nastavit/delaysign v sadě Visual Studio integrované vývojové prostředí  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Klikněte **podpisování** kartě.  
  
3.  Nastavte hodnotu v **zpoždění podepsání** pole.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/ keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
