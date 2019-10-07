---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 66edc45c622b78187469ccc0631beb53b68049b0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002295"
---
# <a name="-delaysign"></a>-delaysign
Určuje, zda bude sestavení zcela nebo částečně podepsáno.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Pokud chcete plně podepsané sestavení, použijte `-delaysign-`. Pokud chcete umístit veřejný klíč do sestavení a rezervovat místo pro podepsaný algoritmus hash, použijte `-delaysign+`. Výchozí hodnota je `-delaysign-`.  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-delaysign` nemá žádný vliv, pokud se používá s parametrem [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby bylo možné podpis přidat později.  
  
 Například pomocí `-delaysign+` může vývojář v organizaci distribuovat nepodepsané testovací verze sestavení, které mohou testeri zaregistrovat s globální mezipamětí sestavení a použít. Po dokončení práce na sestavení může osoba odpovědná za soukromý klíč organizace plně podepsat sestavení. Tato compartmentalization chrání privátní klíč organizace před zveřejněním a umožňuje všem vývojářům pracovat na sestaveních.  
  
 Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Nastavení-delaysign v integrovaném vývojovém prostředí sady Visual Studio  
  
1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.   
  
2. Klikněte na kartu **podepisování** .  
  
3. Nastavte hodnotu v poli **pouze Zpožděné podepsání** .  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
