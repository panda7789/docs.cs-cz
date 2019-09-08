---
title: Ochrana informací o připojení
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 37aab00a967b9912ba01cc3f27f68f8a3e85fdb2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783055"
---
# <a name="protecting-connection-information"></a>Ochrana informací o připojení
Ochrana přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečení aplikace. Připojovací řetězec představuje potenciální chybu zabezpečení, pokud není zabezpečená. Ukládání informací o připojení do prostého textu nebo jejich uchování v rizikech paměti, které napředá celému systému. Připojovací řetězce vložené do zdrojového kódu lze číst pomocí programu [Ildasm. exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) k zobrazení jazyka MSIL (Microsoft Intermediate Language) v kompilovaném sestavení.  
  
 Chyby zabezpečení související s připojovacími řetězci mohou vzniknout v závislosti na použitém typu ověřování, způsobu, jakým jsou připojovací řetězce uchovány v paměti a na disku, a techniky, které jsou použity k jejich sestavení za běhu.  
  
## <a name="use-windows-authentication"></a>Použít ověřování systému Windows  
 Chcete-li omezit přístup ke zdroji dat, je nutné zabezpečit informace o připojení, jako je ID uživatele, heslo a název zdroje dat. Abyste se vyhnuli vystavení informací o uživateli, doporučujeme, abyste používali ověřování systému Windows (někdy označované jako *integrované zabezpečení*), kdykoli je to možné. Ověřování systému Windows je zadáno v připojovacím řetězci pomocí `Integrated Security` klíčových slov nebo `Trusted_Connection` , což eliminuje nutnost použít ID uživatele a heslo. Při použití ověřování systému Windows jsou uživatelé ověřováni systémem Windows a přístup k prostředkům serveru a databáze je určen pomocí udělení oprávnění pro uživatele a skupiny systému Windows.  
  
 V situacích, kdy není možné použít ověřování systému Windows, je nutné použít zvláštní péči, protože uživatelská pověření jsou zveřejněna v připojovacím řetězci. V aplikaci ASP.NET můžete nakonfigurovat účet systému Windows jako pevnou identitu, která se používá pro připojení k databázím a dalším síťovým prostředkům. Můžete povolit zosobnění v elementu identity v souboru **Web. config** a zadat uživatelské jméno a heslo.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Pevný účet identity by měl být účet s nízkou úrovní oprávnění, kterému bylo uděleno pouze nezbytné oprávnění v databázi. Kromě toho byste měli šifrovat konfigurační soubor, aby se uživatelské jméno a heslo nezobrazovaly v nešifrovaném textu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Nepoužívat soubory UDL (Universal Data Link)  
 Vyhněte se ukládání připojovacích <xref:System.Data.OleDb.OleDbConnection> řetězců do souboru UDL (Universal Data Link). UDL jsou uložené ve formátu prostého textu a nelze je šifrovat. Soubor UDL je externí prostředek založený na souboru pro vaši aplikaci a nemůže být zabezpečený ani zašifrovaný pomocí .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Vyhněte se útokům prostřednictvím injektáže pomocí tvůrců připojovacích řetězců  
 Útok prostřednictvím injektáže připojovacího řetězce může nastat, pokud se k sestavení připojovacích řetězců na základě uživatelského vstupu používá dynamická zřetězení řetězců. Pokud vstup uživatele není ověřený a škodlivý text nebo znaky nejsou uvozeny, útočník může potenciálně přistupovat k citlivým datům nebo jiným prostředkům na serveru. Pro vyřešení tohoto problému zavedla ADO.NET 2,0 nové třídy Tvůrce připojovacích řetězců pro ověření syntaxe připojovacího řetězce a zajistěte, aby nebyly zavedeny další parametry. Další informace najdete v tématu [tvůrci připojovacích řetězců](connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Použít trvalé informace o zabezpečení = NEPRAVDA  
 Výchozí hodnota pro `Persist Security Info` je false; doporučujeme použít tuto výchozí hodnotu ve všech připojovacích řetězcích. Nastavení `Persist Security Info` nebo umožňuje`yes` získat informace citlivé na zabezpečení, včetně ID a hesla uživatele, které mají být získány z připojení po `true` jeho otevření. Když `Persist Security Info` je nastavené `false` na `no`nebo, informace o zabezpečení se zahodí po použití k otevření připojení. tím se zajistí, že nedůvěryhodný zdroj nemá přístup k informacím citlivým na zabezpečení.  
  
## <a name="encrypt-configuration-files"></a>Šifrování konfiguračních souborů  
 Připojovací řetězce můžete také ukládat v konfiguračních souborech, což eliminuje nutnost jejich vložení do kódu vaší aplikace. Konfigurační soubory jsou standardní soubory XML, pro které .NET Framework definovala společnou sadu prvků. Připojovací řetězce v konfiguračních souborech jsou obvykle uloženy  **\<v souboru connectionStrings >** elementu v **App. config** pro aplikaci systému Windows nebo v souboru **Web. config** pro aplikaci ASP.NET. Další informace o základech ukládání, načítání a šifrování připojovacích řetězců z konfiguračních souborů najdete v tématu [připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [Šifrování informací o konfiguraci pomocí chráněné konfigurace](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [Zabezpečení v .NET](../../../standard/security/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
