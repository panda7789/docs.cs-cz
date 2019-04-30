---
title: Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929581"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)

Tento nástroj příkazového řádku je možné načíst privátní klíč z úložiště certifikátů. Například *FindPrivateKey.exe* slouží k vyhledání umístění a název souboru privátního klíče přidružené k určité certifikát X.509 v úložišti certifikátů.

> [!IMPORTANT]
> Nástroj FindPrivateKey je dodáván jako ukázku WCF. Další informace o kde najít ukázky a jak ji sestavit, naleznete v tématu [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Syntaxe

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Poznámky

Následující tabulky popisují argumenty a možnosti, které je možné pomocí nástroje pro hledání privátního klíče (FindPrivateKey.exe).

|Argument|Popis|
|--------------|-----------------|
|`storeName`|Název úložiště certifikátů.|
|`storeLocation`|Umístění úložiště certifikátů.|

|Možnost|Popis|
|------------|-----------------|
|`/n <` *subjectName* `>`|Určuje název subjektu certifikátu.|
|`/t <` *Kryptografický otisk* `>`|Určuje kryptografický otisk certifikátu. Certmgr.exe slouží k načtení kryptografického otisku certifikátu.|
|`/f`|Vypíše pouze název souboru.|
|`/d`|Vypíše pouze adresáře.|
|`/a`|Výstupem absolutní název souboru.|

## <a name="examples"></a>Příklady

Následující příkaz načte privátní klíč pro John Doe:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Následující příkaz načte privátní klíč pro místní počítač:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```