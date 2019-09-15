---
title: Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990356"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)

Tento nástroj příkazového řádku je možné použít k načtení privátního klíče z úložiště certifikátů. Například *FindPrivateKey. exe* lze použít k vyhledání umístění a názvu souboru privátního klíče přidruženého k určitému certifikátu X. 509 v úložišti certifikátů.

> [!IMPORTANT]
> Nástroj FindPrivateKey se dodává jako ukázka WCF. Další informace o tom, kde najít ukázku a jak ji sestavit, najdete v tématu [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Syntaxe

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Poznámky

Následující tabulky popisují argumenty a možnosti, které lze použít pomocí nástroje najít privátní klíč (FindPrivateKey. exe).

|Argument|Popis|
|--------------|-----------------|
|`storeName`|Název úložiště certifikátů|
|`storeLocation`|Umístění úložiště certifikátů.|

|Možnost|Popis|
|------------|-----------------|
|`/n <`*Subject*`>`|Určuje název subjektu certifikátu.|
|`/t <`*kryptografický otisk*`>`|Určuje kryptografický otisk certifikátu. K načtení kryptografického otisku certifikátu použijte soubor certmgr. exe.|
|`/f`|Vypíše pouze název souboru.|
|`/d`|Vypíše pouze adresář.|
|`/a`|Vypíše absolutní název souboru.|

## <a name="examples"></a>Příklady

Následující příkaz načte privátní klíč pro Jan Karásek:

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Následující příkaz načte privátní klíč pro místní počítač:

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
