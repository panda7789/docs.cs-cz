---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ff00bead6130601070ac94686ee9622a6fe218
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="findprivatekey"></a>FindPrivateKey
Může být obtížné vyhledat umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů. Nástroj FindPrivateKey.exe usnadňuje tento proces.  
  
> [!IMPORTANT]
>  FindPrivateKey je ukázka, která musí být kompilované před použitím. Najdete v části "pro sestavení projektu FindPrivateKey" části níže pokyny o tom, jak sestavit nástroj FindPrivateKey.  
  
 X.509 – certifikáty jsou nainstalované ve správcem nebo uživatelem na počítači. Certifikát může být ale přístupné služby spuštěné pod jiným účtem (například ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo účty síťové služby v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).  
  
 Tento účet nemusí mít přístup k souboru privátního klíče, protože certifikát nebyl nainstalován v souladu se původně. Nástroj FindPrivateKey vám dává umístění soubor privátního klíče daný certifikát X.509. Můžete přidat oprávnění nebo odeberte oprávnění k tomuto souboru znáte umístění konkrétní certifikáty X.509 soubor privátního klíče.  
  
 Ukázky, které používají certifikáty pro zabezpečení použít nástroj FindPrivateKey v souboru Setup.bat. Jakmile nebyl nalezen soubor privátního klíče, že které můžete použít jiné nástroje, například Cacls.exe nastavit příslušná přístupová práva do souboru.  
  
 Při spuštění [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby pod uživatelským účtem, například vlastním hostováním spustitelný soubor, ujistěte se, že uživatelský účet má oprávnění jen pro čtení k souboru. Při spuštění [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v rámci Internetové informační služby (IIS) výchozí účty, které se spouští služba jsou ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo síťové službě v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], který ve výchozím nastavení nemají přístup k souboru privátního klíče.  
  
## <a name="examples"></a>Příklady  
 Při přístupu k certifikátu, pro které proces nemá oprávnění pro čtení, zobrazí se zprávou výjimky podobně jako v následujícím příkladu.  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 V takovém případě použijte nástroj FindPrivateKey Pokud chcete najít soubor privátního klíče a potom nastavte přístupu pro proces, který je služba spuštěná v části. Například to lze provést pomocí nástroje Cacls.exe jak je znázorněno v následujícím příkladu.  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>Pro sestavení projektu FindPrivateKey  
  
1.  Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do konkrétní jazyk podadresáře v části umístění adresáře, kam jste nainstalovali vzorku.  
  
2.  Dvakrát klikněte na ikonu soubor .sln k otevření souboru v sadě Visual Studio.  
  
3.  V **sestavení** nabídce vyberte možnost **znovu sestavit řešení**. Soubory programu klienta jsou vytvořeny tak client\bin a soubory programu služby jsou vytvořeny tak service\bin.  
  
4.  Sestavování řešení vygeneruje soubor: FindPrivateKey.exe.  
  
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
  
 Pokud nejsou zadány žádné parametry na příkazovém řádku se zobrazí tento text nápovědy.  
  
## <a name="examples"></a>Příklady  
 Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobním úložišti aktuální User.FindPrivateKey Moje CurrentUser - n "CN = localhost".  
  
 Tento příklad vyhledá název souboru certifikátu s názvem subjektu "CN = localhost", v osobní uložení aktuálního a výstupní cesta k adresáři úplné.  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 Tento příklad vyhledá název souboru certifikátu s kryptografickým otiskem "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", v osobním úložišti místního počítače.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>Viz také
