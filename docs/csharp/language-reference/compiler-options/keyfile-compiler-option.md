---
title: -keyfile (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970264"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (Možnosti kompilátoru Jazyka C#)
Určuje název souboru obsahující kryptografický klíč.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|----------|----------------|  
|`file`|Název souboru obsahujícího klíč silného názvu.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití této možnosti kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a podepíše konečné sestavení pomocí soukromého klíče. Chcete-li vygenerovat soubor klíče, zadejte příkaz sn -k `file` na příkazovém řádku.  
  
 Pokud kompilujete s **-target:module**, název souboru klíče je držen v modulu a začleněny do sestavení, který je vytvořen při kompilaci sestavení s [-addmodule](./addmodule-compiler-option.md).  
  
 Můžete také předat informace o šifrování kompilátoru s [-keycontainer](./keycontainer-compiler-option.md). Použijte [-delaysign,](./delaysign-compiler-option.md) pokud chcete částečně podepsané sestavení.  
  
 V případě, že oba -keyfile a -keycontainer jsou určeny (buď příkazového řádku možnost nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve vyzkoušet kontejner klíče. Pokud se to podaří, sestavení je podepsáno informacemi v kontejneru klíčů. Pokud kompilátor nenajde kontejner klíčů, pokusí se soubor zadaný souborem -keyfile. Pokud se to podaří, sestavení je podepsáno s informacemi v souboru klíče a informace o klíči budou nainstalovány v kontejneru klíčů (podobně jako sn-i), takže při další kompilaci bude kontejner klíčů platný.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Další informace naleznete [v tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku **vlastností Podpisu.**  
  
3. Upravte vlastnost **Zvolit vlastnost souboru klíče se silným názvem.**  
  
 Tuto možnost kompilátoru můžete <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>programově přistupovat pomocí aplikace .  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
