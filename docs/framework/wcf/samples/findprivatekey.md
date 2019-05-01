---
title: Ukázkový FindPrivateKey – WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 72e2f49ae7c39b4a0486ec053ff1164c2d833cbe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990090"
---
# <a name="findprivatekey-sample"></a>Ukázka FindPrivateKey

Může být obtížné najít umístění a název souboru privátního klíče přidružené k určité certifikát X.509 v úložišti certifikátů. Nástroj FindPrivateKey.exe usnadňuje tento proces.

> [!IMPORTANT]
> FindPrivateKey je příklad, který má být zkompilovaný před použitím. Najdete v článku [sestavit projekt FindPrivateKey](#to-build-the-findprivatekey-project) pokyny o tom, jak nástroj FindPrivateKey sestavení.

Správce nebo všechny uživatele v počítači jsou nainstalovány certifikáty X.509. Certifikát, ale můžou být dostupné služby spuštěné pod jiným účtem. Například účet NETWORK SERVICE.

Tento účet nesmí mít přístup k souboru privátního klíče, protože certifikát nebyl nainstalován jím původně. Nástroj FindPrivateKey poskytuje umístění souboru s privátním klíčem daný certifikát X.509. Můžete přidat oprávnění nebo odebrat oprávnění k tomuto souboru znáte umístění souboru s privátním klíčem konkrétní certifikátů X.509.

Ukázky, které používají certifikáty pro zabezpečení, použijte nástroj FindPrivateKey v *Setup.bat* souboru. Jakmile byla nalezena souboru s privátním klíčem, můžete použít jiné nástroje, jako *Cacls.exe* nastavit příslušná přístupová práva do souboru.

Při spuštění služby Windows Communication Foundation (WCF) uživatelského účtu, jako je například v místním prostředí spustitelný soubor, ujistěte se, že uživatelský účet má k souboru přístup jen pro čtení. Při spuštění služby WCF v rámci Internetové informační služby (IIS) jsou výchozí účty, které je služba spuštěna pod síťové služby na službě IIS 7 a starší nebo identitu fondu aplikací služby IIS 7.5 a novější verze. Další informace najdete v tématu [identity fondu aplikací součásti](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Příklady

Při přístupu k certifikátu, pro kterou proces nemá oprávnění pro čtení, zobrazí zprávu o výjimce, podobně jako v následujícím příkladu:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Když k tomu dojde, použijte nástroj FindPrivateKey najít soubor privátního klíče a nastavte přístup pro proces, který je služba spuštěná pod. Například to můžete udělat pomocí nástroje Cacls.exe jak je znázorněno v následujícím příkladu:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Sestavit projekt FindPrivateKey

Stáhněte si projekt, najdete v tématu [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Otevřít [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* složku v umístění adresáře, kam jste nainstalovali vzorku.

2. Dvakrát klikněte na ikonu souboru .sln k otevření souboru v sadě Visual Studio.

3. V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**.

4. Sestavování řešení se vygeneruje soubor: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Konvence – položky příkazového řádku

 "[*možnost*]" představuje volitelný sadu parametrů.

 "{*možnost*}" představuje povinný sadu parametrů.

 "*možnost1* &#124; *možnost2*" představuje možností volby mezi sadu možností.

 "\<*hodnotu*>" představuje hodnotu parametru k zapsání.

## <a name="usage"></a>Použití

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

kde:

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

Pokud nejsou zadány žádné parametry příkazového řádku, se zobrazí tento text nápovědy.

## <a name="examples"></a>Příklady

Tento příklad vyhledá název souboru certifikátu se název předmětu "CN = localhost", v osobním úložišti aktuálního uživatele.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Tento příklad vyhledá název souboru certifikátu se název předmětu "CN = localhost", v osobní uložení aktuálního uživatele a výstupní cesta k adresáři úplné.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Tento příklad vyhledá název souboru certifikátu s kryptografickým otiskem z "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", v osobním úložišti místního počítače.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
