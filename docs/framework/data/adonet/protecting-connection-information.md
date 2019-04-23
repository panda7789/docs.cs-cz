---
title: Ochrana informací o připojení
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: ccb039a79c76c31b905783b81710571d8c5ab82b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184441"
---
# <a name="protecting-connection-information"></a>Ochrana informací o připojení
Zabezpečení přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečování aplikace. Připojovací řetězec představuje potenciální ohrožení zabezpečení, není-li zabezpečena. Ukládání informací o připojení ve formátu prostého textu nebo uchování v paměti rizika porušení zabezpečení celého systému. Připojovací řetězce vloženy do zdrojového kódu, lze jej číst pomocí [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zobrazíte jazyk Microsoft intermediate language (MSIL) v kompilovaném sestavení.  
  
 Ohrožení zabezpečení, které mohou vzniknout zahrnující připojovací řetězce na základě typu ověřování používá, jak připojovací řetězce jsou zachované v paměti a na disku a techniky slouží k vytvoření za běhu.  
  
## <a name="use-windows-authentication"></a>Používat ověřování Windows  
 Chcete-li pomoci omezit přístup na zdroji dat, musíte zabezpečit informace o připojení, jako je například název zdroje ID, heslo a dat uživatele. Abyste zabránili zveřejnění informací o uživateli, doporučujeme používat ověřování Windows (někdy označovány jako *integrované zabezpečení*) kdykoli je to možné. Ověřování Windows je v připojovacím řetězci zadané pomocí `Integrated Security` nebo `Trusted_Connection` klíčová slova, takže odpadá nutnost používat uživatelské jméno a heslo. Pokud používáte ověřování Windows, uživatelé budou ověření ve Windows a přístup k prostředkům serveru a databáze je určen tím, že uděluje oprávnění pro uživatele Windows a skupiny.  
  
 V situacích, kdy není možné používat ověřování Windows musíte použít velmi opatrně, protože v připojovacím řetězci jsou vystaveny přihlašovací údaje uživatele. V aplikaci technologie ASP.NET můžete nakonfigurovat účet Windows jako dlouhodobý identitou, která se používá pro připojení k databázím a jiným síťovým prostředkům. Povolení zosobnění v elementu identity v **web.config** souboru a zadejte uživatelské jméno a heslo.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Účet pevné identity musí být účet s nízkou úrovní oprávnění, který má oprávnění pouze nezbytné v databázi. Kromě toho by měla šifrovat konfiguračního souboru tak, aby uživatelské jméno a heslo nejsou zveřejněné ve formátu prostého textu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Soubory není použití univerzální datové propojení (UDL)  
 Vyhněte se ukládání připojovacích řetězců pro <xref:System.Data.OleDb.OleDbConnection> v souboru univerzální datové propojení (UDL). UDL jsou uložené ve formátu prostého textu a nelze zašifrovat. Soubor UDL je externí souborových prostředků do vaší aplikace a nelze zabezpečit nebo šifrované pomocí rozhraní .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Vyhněte se útoky prostřednictvím injektáže s tvůrci připojovacích řetězců  
 Útok prostřednictvím injektáže řetězec připojení může dojít, když dynamická zřetězení sloužící k sestavení na základě uživatelského zadání připojovacích řetězců. Pokud uživatelský vstup není ověřená a škodlivý text nebo znaky nejsou uvozeny řídicími znaky, útočník můžou mít přístup k citlivým datům nebo další prostředky na serveru. Chcete-li tento problém vyřešit, ADO.NET 2.0 zavedeny nové třídy tvůrce řetězec připojení k ověření syntaxe připojovacího řetězce a ujistěte se, že nejsou zavedena další parametry. Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Použití trvalé informace o zabezpečení = False  
 Výchozí hodnota pro `Persist Security Info` má hodnotu false; doporučujeme používat toto výchozí nastavení ve všech připojovací řetězce. Nastavení `Persist Security Info` k `true` nebo `yes` umožňuje zabezpečené informace, včetně ID uživatele a heslo, chcete-li získat z připojení po jeho otevření. Když `Persist Security Info` je nastavena na `false` nebo `no`, informace o zabezpečení se zruší po se používá k otevření připojení, zajištění, že nedůvěryhodného zdroje nemá přístup k informacím o citlivé na zabezpečení.  
  
## <a name="encrypt-configuration-files"></a>Šifrování konfiguračních souborů  
 Můžete také uložit připojovací řetězce v konfiguračních souborech, není potřeba, k vložení do kódu vaší aplikace. Konfigurační soubory jsou standardní soubory XML, pro které má definované rozhraní .NET Framework společnou sadu elementů. Připojovací řetězce v konfiguračních souborech jsou obvykle uložena v  **\<connectionStrings >** prvek **app.config** pro aplikace Windows nebo  **soubor Web.config** soubor pro aplikaci ASP.NET. Další informace o základní ukládání, načítání a šifrování připojovacího řetězce z konfiguračních souborů, najdete v části [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Informace o konfiguraci chráněných konfigurace šifrování](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [Zabezpečení v rozhraní .NET](../../../standard/security/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
