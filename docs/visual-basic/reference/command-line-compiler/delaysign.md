---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 3ee94df096b756be544964cfbbd405355e3f728f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581275"
---
# <a name="-delaysign"></a>-delaysign

Určuje, zda bude sestavení zcela nebo částečně podepsáno.

## <a name="syntax"></a>Syntaxe

```console
-delaysign[+ | -]
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`  
Nepovinný parametr. Použijte `-delaysign-` , pokud chcete sestavení plně podepsaného. Použijte `-delaysign+` , pokud chcete umístit veřejný klíč do sestavení a rezervovat místo pro podepsaný algoritmus hash. Výchozí formát je `-delaysign-`.

## <a name="remarks"></a>Poznámky

`-delaysign` Možnost nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md).

Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby bylo možné podpis přidat později.

Například pomocí nástroje `-delaysign+`může vývojář v organizaci distribuovat nepodepsané testovací verze sestavení, které mohou testeri zaregistrovat s globální mezipamětí sestavení a použít. Po dokončení práce na sestavení může osoba odpovědná za soukromý klíč organizace plně podepsat sestavení. Tato compartmentalization chrání privátní klíč organizace před zveřejněním a umožňuje všem vývojářům pracovat na sestaveních.

Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Nastavení-delaysign v integrovaném vývojovém prostředí sady Visual Studio

1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

2. Klikněte na kartu **podepisování** .

3. Nastavte hodnotu v poli **pouze Zpožděné podepsání** .

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
