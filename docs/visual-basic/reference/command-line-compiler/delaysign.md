---
title: -delaysign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d659e97f3b3a360456a1fcdaa9756934bb096334
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-delaysign"></a>-delaysign
Určuje, zda bude sestavení zcela nebo částečně podepsáno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Použití `-delaysign-` Pokud chcete plně podepsané sestavení. Použití `-delaysign+` Pokud chcete umístit veřejný klíč v sestavení a rezervy místa pro podepsané hash. Výchozí hodnota je `-delaysign-`.  
  
## <a name="remarks"></a>Poznámky  
 `-delaysign` Možnost nemá žádný vliv, pokud není použita s [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash s privátním klíčem. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Při sestavení zpoždění, které jsou podepsané, kompilátor nepodporuje výpočetní a uložení podpis ale rezervy místa v souboru, takže podpis lze přidat později.  
  
 Například pomocí `-delaysign+`, vývojáři v organizaci můžete distribuovat nepodepsané testovací verze sestavení, které testery můžete zaregistrovat s globální mezipaměti sestavení a použít. Po dokončení práce na sestavení může osoba odpovědná za soukromého klíče organizace plně podepsat sestavení. Tato takové soukromého klíče organizace chrání před zpřístupnění současně všechny vývojářům pracovat na sestavení.  
  
 V tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Chcete-li nastavit - delaysign v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte **podpisování** kartě.  
  
3.  Nastavte hodnotu v **zpoždění podepsání** pole.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
