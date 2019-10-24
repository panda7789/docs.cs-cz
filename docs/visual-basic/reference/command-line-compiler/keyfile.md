---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 2617c42d7b176806cfac0fc2247760727608261a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775646"
---
# <a name="-keyfile"></a>-keyfile
Určuje soubor obsahující klíč nebo dvojici klíčů, které sestavení poskytují silný název.  
  
## <a name="syntax"></a>Syntaxe  
  
```console 
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Požadováno. Soubor, který obsahuje klíč. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vloží veřejný klíč do manifestu sestavení a pak podepíše konečné sestavení pomocí privátního klíče. Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud kompilujete s `-target:module`, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Použijte [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , pokud chcete použít částečně podepsané sestavení.  
  
 Tuto možnost můžete také zadat jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro libovolný modul Microsoft Intermediate Language.  
  
 V případě, že jsou zadány oba `-keyfile` a [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md) klíčové pole (buď parametr příkazového řádku nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve pokusí kontejner klíčů. Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů. Pokud kompilátor nenalezne kontejner klíčů, pokusí se soubor zadaný pomocí `-keyfile`. Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči jsou nainstalovány v kontejneru klíčů (podobně jako `sn -i`), takže při další kompilaci bude kontejner klíčů platný.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> Možnost `-keyfile` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.

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
