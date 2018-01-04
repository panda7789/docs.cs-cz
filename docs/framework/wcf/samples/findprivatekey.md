---
title: "Ukázka FindPrivateKey - WCF"
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32e1a4a3de01371d67be8d19613b1f29c1ce3c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="findprivatekey-sample"></a>Ukázka FindPrivateKey

Může být obtížné vyhledat umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů. Nástroj FindPrivateKey.exe usnadňuje tento proces.

> [!IMPORTANT]
> FindPrivateKey je ukázka, která musí být kompilované před použitím. Najdete v článku [pro sestavení projektu FindPrivateKey](#to-build-the-findprivatekey-project) část pokyny, jak sestavit nástroj FindPrivateKey.

X.509 – certifikáty jsou nainstalované ve správcem nebo uživatelem na počítači. Certifikát však může být přístupné služby spuštěné pod jiným účtem. Například účet síťové služby.

Tento účet nemusí mít přístup k souboru privátního klíče, protože certifikát nebyl nainstalován v souladu se původně. Nástroj FindPrivateKey vám dává umístění soubor privátního klíče daný certifikát X.509. Můžete přidat oprávnění nebo odeberte oprávnění k tomuto souboru znáte umístění konkrétní certifikáty X.509 soubor privátního klíče.

Ukázky, které používají certifikáty pro zabezpečení použít nástroj FindPrivateKey v *Setup.bat* souboru. Jakmile byl nalezen soubor privátního klíče, můžete použít jiné nástroje, jako *Cacls.exe* nastavit příslušná přístupová práva do souboru.

Při spuštění služby Windows Communication Foundation (WCF) pod uživatelským účtem, například vlastním hostováním spustitelný soubor, ujistěte se, že uživatelský účet má oprávnění jen pro čtení k souboru. Při spuštění služby WCF v rámci Internetové informační služby (IIS) jsou výchozí účty, které se spouští služba NETWORK SERVICE ve službě IIS 7 a starší verze nebo identita fondu aplikací služby IIS 7.5 a novější verze. Další informace najdete v tématu [identity fondu aplikací součásti](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Příklady

Při přístupu k certifikátu, pro které proces nemá oprávnění pro čtení, zobrazí se zprávou výjimky podobně jako v následujícím příkladu:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

V takovém případě najít soubor privátního klíče pomocí nástroje FindPrivateKey a nastavte přístupu pro proces, který je služba spuštěná v části. Například to lze provést pomocí nástroje Cacls.exe jak je znázorněno v následujícím příkladu:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Pro sestavení projektu FindPrivateKey

Je možné stáhnout projektu [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* složku s umístěním adresáře, kam jste nainstalovali vzorku.

2. Dvakrát klikněte na ikonu soubor .sln k otevření souboru v sadě Visual Studio.

3. V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**.

4. Sestavování řešení vygeneruje soubor: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Konvence – položky příkazového řádku

 "[*možnost*]" představuje volitelný sadu parametrů.

 "{*možnost*}" představuje sadu parametrů povinné.

 "*možnost 1* &#124; *option2*"představuje volba mezi sady možností.

 "\<*hodnotu*>" představuje hodnotu parametru, které je třeba zadat.

## <a name="usage"></a>Použití

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Kde:

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

Pokud nejsou zadány žádné parametry příkazového řádku, se zobrazí tento text nápovědy.

## <a name="examples"></a>Příklady

Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobním úložišti aktuálního uživatele.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobní uložení aktuálního uživatele a výstupní cesta k adresáři úplná.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Tento příklad vyhledá název souboru certifikátu s kryptografickým otiskem "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", v osobním úložišti místního počítače.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
