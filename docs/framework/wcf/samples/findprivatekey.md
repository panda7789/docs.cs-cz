---
title: Ukázka FindPrivateKey – WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989874"
---
# <a name="findprivatekey-sample"></a>Ukázka FindPrivateKey

Může být obtížné najít umístění a název souboru privátního klíče přidruženého k určitému certifikátu X. 509 v úložišti certifikátů. Nástroj FindPrivateKey. exe Tento proces usnadňuje.

> [!IMPORTANT]
> FindPrivateKey je ukázka, kterou je třeba před použitím zkompilovat. Pokyny k vytvoření nástroje FindPrivateKey najdete v části [Vytvoření projektu FindPrivateKey](#to-build-the-findprivatekey-project) .

Certifikáty X. 509 jsou nainstalovány správcem nebo jakýmkoli uživatelem v počítači. K certifikátu ale může mít přístup služba spuštěná v jiném účtu. Například účet síťové služby.

Tento účet nemusí mít přístup k souboru privátního klíče, protože certifikát nebyl původně nainstalován. Nástroj FindPrivateKey poskytuje umístění daného souboru privátního klíče certifikátu X. 509. Jakmile budete znát umístění konkrétního souboru privátního klíče certifikátů X. 509, můžete oprávnění k tomuto souboru přidat nebo je z něj odebrat.

V ukázkách, které používají certifikáty k zabezpečení, se používá nástroj FindPrivateKey v souboru *Setup. bat* . Po nalezení souboru privátního klíče můžete použít jiné nástroje, jako je například *cacls. exe* , a nastavit tak příslušná přístupová práva na daný soubor.

Při spuštění služby Windows Communication Foundation (WCF) pod uživatelským účtem, jako je například spustitelný soubor v místním prostředí, zajistěte, aby měl uživatelský účet k souboru přístup jen pro čtení. Při spuštění služby WCF pod Internetová informační služba (IIS) výchozí účty, ve kterých je služba spuštěná, jsou síťové služby ve službě IIS 7 a starší verze nebo identita fondu aplikací ve službě IIS 7,5 a novějších verzích. Další informace najdete v tématu [identity fondu aplikací](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Příklady

Při přístupu k certifikátu, pro který proces nemá oprávnění ke čtení, se zobrazí zpráva o výjimce, která je podobná následujícímu příkladu:

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

V takovém případě použijte nástroj FindPrivateKey k vyhledání souboru privátního klíče a pak nastavte přístupová práva pro proces, pod kterým je služba spuštěná. To lze provést například pomocí nástroje Cacls. exe, jak je znázorněno v následujícím příkladu:

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Sestavení projektu FindPrivateKey

Pokud si chcete stáhnout projekt, přejděte na [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Otevřete Průzkumníka souborů a přejděte do složky *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* v umístění adresáře, kam jste si nainstalovali ukázku.

2. Dvojím kliknutím na ikonu souboru. sln otevřete soubor v aplikaci Visual Studio.

3. V nabídce **sestavení** vyberte znovu **Sestavit řešení**.

4. Sestavení řešení vygeneruje soubor: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Konvence – položky příkazového řádku

 "[*možnost*]" představuje volitelnou sadu parametrů.

 {*Option*} představuje povinnou sadu parametrů.

 "*možnost1* &#124; *možnost2*" představuje volbu mezi sadami možností.

 Hodnota > představuje hodnotu parametru, která se má zadat.\<

## <a name="usage"></a>Použití

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

,

| Parametr         | Popis                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | Název subjektu certifikátu                                               |
| `<thumbprint>`  | Kryptografický otisk certifikátu (k jeho zjištění můžete použít nástroj certmgr. exe) |
| `-f`            | pouze název výstupního souboru                                                             |
| `-d`            | pouze výstupní adresář                                                             |
| `-a`            | název absolutního souboru výstupu                                                         |

Pokud nejsou zadány žádné parametry na příkazovém řádku, zobrazí se text nápovědy s těmito informacemi.

## <a name="examples"></a>Příklady

Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost" v osobním úložišti aktuálního uživatele.

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Tento příklad najde název souboru certifikátu s názvem subjektu "CN = localhost", v osobním úložišti aktuálního uživatele a výstupem úplné cesty k adresáři.

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Tento příklad najde název souboru certifikátu s kryptografickým otiskem "03 33 98 63 D0 47 E7 48 71 33 62 64 76 5c 4C 9d 42 1d 6b 52", v osobním úložišti místního počítače.

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
