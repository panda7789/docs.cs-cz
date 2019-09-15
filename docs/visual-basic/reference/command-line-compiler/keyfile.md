---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 30b890cf3d523d1e33b433a1ff6109759bd9a5e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972333"
---
# <a name="-keyfile"></a>-keyfile
Určuje soubor obsahující klíč nebo dvojici klíčů, které sestavení poskytují silný název.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Povinný parametr. Soubor, který obsahuje klíč. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vloží veřejný klíč do manifestu sestavení a pak podepíše konečné sestavení pomocí privátního klíče. Chcete-li vygenerovat soubor klíče `sn -k file` , zadejte do příkazového řádku. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud kompilujete s `-target:module`, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilování sestavení pomocí [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Použijte [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , pokud chcete použít částečně podepsané sestavení.  
  
 Tuto možnost lze také zadat jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro libovolný modul Microsoft Intermediate Language.  
  
 V případě, `-keyfile` že jsou zadány oba a [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md) klíčové pole (buď parametr příkazového řádku nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve pokusí kontejner klíčů. Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů. Pokud kompilátor nenajde kontejner klíčů, pokusí se o soubor zadaný pomocí `-keyfile`. Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči jsou nainstalovány v kontejneru klíčů (podobně jako `sn -i`), takže při další kompilaci bude kontejner klíčů platný.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> Tato `-keyfile` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `Input.vb` a určí soubor klíče.  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
