---
title: Ochrana informací o připojení
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 1039d3fd797a16391876b59aa018b30b7f397aeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149216"
---
# <a name="protecting-connection-information"></a>Ochrana informací o připojení
Ochrana přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec představuje potenciální chybu zabezpečení, pokud není zabezpečena. Ukládání informací o připojení ve formátu prostého textu nebo jejich uchování v paměti může ohrozit celý systém. Připojovací řetězce vložené do zdrojového kódu lze číst pomocí [ildasm.exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) pro zobrazení zprostředkujícího jazyka Microsoft (MSIL) v kompilovaném sestavení.  
  
 Chyby zabezpečení zahrnující připojovací řetězce mohou vzniknout na základě typu použitého ověřování, způsobu, jakým jsou připojovací řetězce v paměti a na disku zachovány, a technik používaných k jejich vytvoření za běhu.  
  
## <a name="use-windows-authentication"></a>Použít ověřování systému Windows  
 Chcete-li omezit přístup ke zdroji dat, je nutné zabezpečit informace o připojení, jako je ID uživatele, heslo a název zdroje dat. Aby se zabránilo odhalení informací o uživateli, doporučujeme používat ověřování systému Windows (někdy označované jako *integrované zabezpečení)* všude tam, kde je to možné. Ověřování systému Windows je určeno `Integrated Security` v `Trusted_Connection` připojovacím řetězci pomocí klíčových slov nebo, což eliminuje potřebu používat ID uživatele a heslo. Při použití ověřování systému Windows jsou uživatelé ověřováni systémem Windows a přístup k serverovým a databázovým prostředkům je určen udělením oprávnění uživatelům a skupinám systému Windows.  
  
 V situacích, kdy není možné použít ověřování systému Windows, je nutné věnovat zvláštní pozornost, protože pověření uživatele jsou vystavena v připojovacím řetězci. V ASP.NET aplikaci můžete nakonfigurovat účet systému Windows jako pevnou identitu, která se používá pro připojení k databázím a dalším síťovým prostředkům. Povolíte zosobnění prvku identity v souboru **web.config** a zadáte uživatelské jméno a heslo.  
  
```xml  
<identity impersonate="true"
        userName="MyDomain\UserAccount"
        password="*****" />  
```  
  
 Účet pevné identity by měl být účet s nízkými oprávněními, kterému byla udělena pouze potřebná oprávnění v databázi. Kromě toho byste měli zašifrovat konfigurační soubor tak, aby uživatelské jméno a heslo nebyly vystaveny ve prostém textu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Nepoužívejte soubory univerzálního datového spojení (UDL)  
 Vyhněte se ukládání připojovacích řetězců pro <xref:System.Data.OleDb.OleDbConnection> soubor Univerzální datové spojení (UDL). UDL jsou uloženy ve prostém textu a nelze je zašifrovat. Soubor UDL je externí prostředek založený na souborech pro vaši aplikaci a nelze jej zabezpečit ani zašifrovat pomocí rozhraní .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Vyhněte se útokům injektáží s nástroji pro zařazování připojovacích řetězců  
 K útoku injektáží připojovacího řetězce může dojít při dynamickém zřetězení řetězce se používá k vytvoření připojovacích řetězců na základě vstupu uživatele. Pokud vstup uživatele není ověřen a škodlivý text nebo znaky nejsou uvozeny, útočník může potenciálně přistupovat k citlivým datům nebo jiným prostředkům na serveru. K vyřešení tohoto problému ADO.NET 2.0 zavedla nové třídy tvůrce připojovacího řetězce k ověření syntaxe připojovacího řetězce a zajištění toho, aby nebyly zavedeny další parametry. Další informace naleznete v [tématu Connection String Builders](connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Použít informace o trvalém zabezpečení=Nepravda  
 Výchozí hodnota `Persist Security Info` pro je false; Doporučujeme použít toto výchozí nastavení ve všech připojovacích řetězcích. Nastavení `Persist Security Info` `true` nebo `yes` umožňuje nebo umožňuje informace citlivé na zabezpečení, včetně ID uživatele a heslo, které mají být získány z připojení po jeho otevření. Pokud `Persist Security Info` je `false` nastavena na nebo `no`, informace o zabezpečení jsou po použití k otevření připojení zahozeny a zajišťují, že nedůvěryhodný zdroj nemá přístup k informacím citlivým na zabezpečení.  
  
## <a name="encrypt-configuration-files"></a>Šifrování konfiguračních souborů  
 Připojovací řetězce můžete také uložit do konfiguračních souborů, což eliminuje potřebu jejich vložení do kódu aplikace. Konfigurační soubory jsou standardní soubory XML, pro které rozhraní .NET Framework definovalo společnou sadu prvků. Připojovací řetězce v konfiguračních souborech jsou obvykle ** \<uloženy** uvnitř řetězce připojení>prvek v **application.config** pro aplikaci systému Windows nebo **web.config** soubor pro ASP.NET aplikace. Další informace o základech ukládání, načítání a šifrování připojovacích řetězců z konfiguračních souborů naleznete v [tématu Připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [Šifrování informací o konfiguraci pomocí chráněné konfigurace](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [Zabezpečení v .NET](../../../standard/security/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
