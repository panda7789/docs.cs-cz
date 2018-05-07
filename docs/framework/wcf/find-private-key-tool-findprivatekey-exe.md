---
title: Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)

Tento nástroj příkazového řádku lze získat privátní klíč z úložiště certifikátů. Například *FindPrivateKey.exe* můžete použít k vyhledání umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů.

> [!IMPORTANT]
> Nástroj FindPrivateKey je dodávána jako Ukázka WCF. Další informace o kde najít ukázky a jak ji od sestavit najdete v tématu [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Syntaxe

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Poznámky

Následující tabulky popisují argumenty a možnosti, které je možné pomocí nástroje Najít privátního klíče (FindPrivateKey.exe).

|Argument|Popis|
|--------------|-----------------|
|`storeName`|Název úložiště certifikátů.|
|`storeLocation`|Umístění úložiště certifikátů.|

|Možnost|Popis|
|------------|-----------------|
|`/n <` *SubjectName* `>`|Určuje název předmětu certifikátu.|
|`/t <` *Kryptografický otisk* `>`|Určuje kryptografický otisk certifikátu. Pomocí Certmgr.exe získat kryptografický otisk certifikátu.|
|`/f`|Výstupy pouze název souboru.|
|`/d`|Výstupy pouze adresáři.|
|`/a`|Výstupy název souboru na absolutní.|

## <a name="examples"></a>Příklady

Tento příkaz načte privátní klíč pro John Doe:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Tento příkaz načte privátní klíč pro místní počítač:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```