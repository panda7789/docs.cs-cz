---
title: Změny oboru názvů System.Uri ve verzi 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642760"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Změny oboru názvů System.Uri ve verzi 2.0

Ve <xref:System.Uri?displayProperty=nameWithType> třídě bylo provedeno několik změn. Tyto změny opravily nesprávné chování, lepší použitelnost a rozšířené zabezpečení.

## <a name="obsolete-and-deprecated-members"></a>Zastaralí a zastaralí členové

 Konstruktory:

- Všechny konstruktory, `dontEscape` které mají parametr.

 Metody:

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a>Změny

- U schémat URI, o kterých je známo, že nemají část dotazu (soubor, ftp a další), <xref:System.Uri.Query%2A> je znak '?' vždy uvozen a není považován za začátek dílu.

- Pro implicitní soubor URI `c:\directory\file@name.txt`(formuláře ) znak fragmentu ('#') je vždy <xref:System.Uri.LocalPath%2A> uvozen, pokud není požadováno úplné neuvození nebo není `true`.

- Podpora názvu hostitele UNC byla odebrána. byla přijata specifikace IDN pro zastupování mezinárodních názvů hostitelů.

- <xref:System.Uri.LocalPath%2A>vždy vrátí zcela unescaped řetězec.

- <xref:System.Uri.ToString%2A>neunescape uvozený znak %, '?' nebo '#'.

- <xref:System.Uri.Equals%2A>nyní zahrnuje <xref:System.Uri.Query%2A> část kontroly rovnosti.

- Operátory "==" a "!=" jsou <xref:System.Uri.Equals%2A> přepsány a propojeny s metodou.

- <xref:System.Uri.IsLoopback%2A>nyní vytváří konzistentní výsledky.

- Identifikátor URI`file:///path`" " již `file://path`není přeložen do .

- "#" je nyní rozpoznán jako zakončení názvu hostitele. To znamená, `http://contoso.com#fragment` že je `http://contoso.com/#fragment`nyní převeden na .

- Byla opravena chyba při kombinování základního identifikátoru URI s fragmentem.

- Chyba je <xref:System.Uri.HostNameType%2A> opravena.

- Chyba v analýzě NNTP je pevná.

- Identifikátor URI formuláře HTTP:contoso.com nyní vyvolá výjimku analýzy.

- Rozhraní Framework správně zpracovává userinfo v uri.

- Komprese cesty URI je opravena tak, že přerušený identifikátor URI nemůže procházet systémem souborů nad kořenem.

## <a name="see-also"></a>Viz také

- <xref:System.Uri?displayProperty=nameWithType>
