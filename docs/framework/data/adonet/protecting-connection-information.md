---
title: Ochrana informací o připojení
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 4cf503af6f57eefb0990a8e7e728ea5c1474bfa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="protecting-connection-information"></a>Ochrana informací o připojení
Zabezpečení přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec uvede potenciální ohrožení zabezpečení, pokud není zabezpečená. Ukládání informací o připojení ve formátu prostého textu nebo uchování v paměti rizika ohrožení celého systému. Připojovací řetězce, které jsou součástí vašeho zdrojového kódu lze číst pomocí [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zobrazíte Microsoft (MSIL intermediate language) v kompilovaném sestavení.  
  
 Chyby zabezpečení, které mohou nastat zahrnující připojovací řetězce na základě typu ověřování použít, jak připojovací řetězce jsou nastavené jako trvalé v paměti a na disku a techniky použitý k vytvoření je za běhu.  
  
## <a name="use-windows-authentication"></a>Ověřování systému Windows  
 Můžete omezit přístup k zdroj dat, je nutné zabezpečit informace o připojení, jako je například název zdroje dat, ID a heslo uživatele. Aby se zabránilo vystavení informace o uživateli, doporučujeme použít ověřování systému Windows (někdy označovány jako *integrované zabezpečení*) Pokud je to možné. Ověřování systému Windows je zadaný v připojovacím řetězci pomocí `Integrated Security` nebo `Trusted_Connection` klíčová slova, takže není nutné používat ID uživatele a heslo. Pokud používáte ověřování systému Windows, uživatelé se ověřují v systému Windows a přístup k prostředkům serveru a databáze je dáno udělení oprávnění uživatelům Windows a skupiny.  
  
 V situacích, kde není možné použít ověřování systému Windows musíte použít zvláštní pozornost, protože přihlašovací údaje uživatele jsou zveřejněné v připojovacím řetězci. V aplikaci ASP.NET můžete nakonfigurovat účet systému Windows jako pevné identitou, která se používá k připojení k databázím a jiným síťovým prostředkům. Povolení zosobnění v elementu identity v **web.config** souboru a zadejte uživatelské jméno a heslo.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Opravené identity účet by měl být nízkými oprávněními účet, kterému byla udělena pouze nezbytná oprávnění v databázi. Kromě toho by měla šifrování konfiguračního souboru tak, aby se nezobrazí uživatelské jméno a heslo ve formátu prostého textu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Soubory není použití Universal Data odkaz (UDL)  
 Vyhněte se ukládání připojovací řetězce pro <xref:System.Data.OleDb.OleDbConnection> v souboru Universal Data odkaz (UDL). UDLs se ukládají ve formátu prostého textu a nedá se zašifrovat. Soubor UDL je externí prostředek na základě souborů k vaší aplikaci, a nelze zabezpečit nebo šifrovat pomocí rozhraní .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Vyhněte se prostřednictvím injektáže s Tvůrci řetězců pro připojení  
 Útok prostřednictvím injektáže řetězec připojení může dojít, když dynamické zřetězení slouží k vytvoření připojovací řetězce, které jsou založené na vstup uživatele. Pokud uživatelský vstup není ověřená a škodlivý text nebo znaky není řídicí sekvencí, útočník mají přístup k citlivým datům nebo jiným prostředkům na serveru. Chcete-li vyřešit tento problém, ADO.NET 2.0 zavedeny nové třídy tvůrce řetězec připojení ověřte syntaxi připojovacího řetězce a ujistěte se, že nejsou zavedena další parametry. Další informace najdete v tématu [Tvůrci řetězců pro připojení](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Použití zachovat bezpečnostní údaje = False  
 Výchozí hodnota pro `Persist Security Info` NEPRAVDA; doporučujeme používat toto výchozí nastavení ve všech připojovací řetězce. Nastavení `Persist Security Info` k `true` nebo `yes` umožňuje informace citlivé na zabezpečení, včetně ID uživatele a heslo, získat z připojení po byl otevřen. Když `Persist Security Info` je nastaven na `false` nebo `no`, informace o zabezpečení je odstraněn po se používá k otevření připojení, zajistíte, že nedůvěryhodných nemá přístup k citlivé informace.  
  
## <a name="encrypt-configuration-files"></a>Šifrování konfiguračních souborů  
 Také můžete uložit připojovací řetězce v konfiguračních souborech, což eliminuje potřebu vložit do kódu aplikace. Konfigurační soubory jsou standardní soubory XML, pro které je rozhraní .NET Framework definovaný společnou sadu elementů. Připojovací řetězce v konfiguračních souborech uvnitř obvykle ukládají  **\<connectionStrings >** element v **app.config** pro aplikace systému Windows nebo  **soubor Web.config** soubor pro aplikaci ASP.NET. Další informace o základní informace o ukládání, načítání a šifrování připojovacího řetězce z konfiguračních souborů, najdete v části [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Šifrované informace o konfiguraci pomocí chráněné konfigurace](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 [Připravte si kód pro rozhraní .NET Framework a zabezpečení v nativním režimu](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
