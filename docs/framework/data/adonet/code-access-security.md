---
title: Zabezpečení přístupu kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: 6fc54bb9e38768e390201ea77243d3df4cd67f10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151738"
---
# <a name="code-access-security-and-adonet"></a>Zabezpečení přístupu ke kódu a ADO.NET
Rozhraní .NET Framework nabízí zabezpečení založené na rolích, stejně jako zabezpečení přístupu kódu (CAS), které jsou implementovány pomocí společné infrastruktury poskytované clr (COMMON Language runtime). Ve světě nespravovaného kódu se většina aplikací spouští s oprávněními uživatele nebo objektu zabezpečení. V důsledku toho mohou být počítačové systémy poškozeny a soukromá data ohrožena, pokud je škodlivý software nebo software naplněný chybami spuštěn uživatelem se zvýšenými oprávněními.  
  
 Naproti tomu spravovaný kód spuštěný v rozhraní .NET Framework zahrnuje zabezpečení přístupu kódu, které platí pro samotný kód. Zda je povoleno spustit kód nebo ne, závisí na původu kódu nebo jiných aspektech identity kódu, nikoli pouze na identitě hlavního povinného. To snižuje pravděpodobnost, že spravovaný kód může být zneužit.  
  
## <a name="code-access-permissions"></a>Oprávnění pro přístup kódu  
 Při spuštění kódu představuje důkazy, které jsou vyhodnoceny systémem zabezpečení CLR. Tento důkaz obvykle zahrnuje původ kódu včetně adresy URL, webu a zóny a digitálních podpisů, které zajišťují identitu sestavení.  
  
 CLR umožňuje kód provádět pouze ty operace, které kód má oprávnění k provedení. Kód může požadovat oprávnění a tyto požadavky jsou dodrženy na základě zásad zabezpečení nastavených správcem.  
  
> [!NOTE]
> Kód spuštěný v CLR nemůže udělit oprávnění sám sobě. Kód může například požadovat a získat méně oprávnění, než umožňuje zásady zabezpečení, ale nikdy mu nebude uděleno více oprávnění. Při udělování oprávnění začněte bez oprávnění vůbec a přidejte nejužší oprávnění pro konkrétní prováděnou úlohu. Počínaje všemi oprávněními a následným odepřením jednotlivých aplikací vede k nezabezpečeným aplikacím, které mohou obsahovat neúmyslné bezpečnostní díry, udělit více oprávnění, než je požadováno. Další informace naleznete [v tématu Konfigurace zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) a správy zásad [zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Existují tři typy přístupových oprávnění kódu:  
  
- `Code access permissions`odvozují <xref:System.Security.CodeAccessPermission> se z třídy. Oprávnění jsou vyžadována pro přístup k chráněným prostředkům, jako jsou soubory a proměnné prostředí, a k provádění chráněných operací, jako je například přístup k nespravovanému kódu.  
  
- `Identity permissions`charakteristiky, které identifikují sestavení. Oprávnění jsou udělena sestavení na základě důkazů, které mohou zahrnovat položky, jako je například digitální podpis nebo kde pochází kód. Oprávnění identity také <xref:System.Security.CodeAccessPermission> odvodit ze základní třídy.  
  
- `Role-based security permissions`jsou založeny na tom, zda objekt zabezpečení má zadanou identitu nebo je členem zadané role. Třída <xref:System.Security.Permissions.PrincipalPermission> umožňuje deklarativní i imperativní kontroly oprávnění proti aktivní objekt zabezpečení.  
  
 Chcete-li zjistit, zda je kód oprávněn k přístupu k prostředku nebo k provedení operace, systém zabezpečení za běhu prochází zásobníkem volání a porovnává udělená oprávnění každého volajícího s požadovaným oprávněním. Pokud některý volající v zásobníku volání nemá požadované <xref:System.Security.SecurityException> oprávnění, je vyvolána a přístup je odmítnut.  
  
### <a name="requesting-permissions"></a>Vyžadování oprávnění  
 Účelem vyžádání oprávnění je informovat za běhu, která oprávnění vaše aplikace vyžaduje ke spuštění, a zajistit, aby obdržela pouze oprávnění, která skutečně potřebuje. Například pokud aplikace potřebuje zapisovat data na <xref:System.Security.Permissions.FileIOPermission>místní disk, vyžaduje . Pokud toto oprávnění nebylo uděleno, aplikace se nezdaří při pokusu o zápis na disk. Pokud však aplikace `FileIOPermission` požaduje a toto oprávnění nebylo uděleno, aplikace vygeneruje výjimku na začátku a nebude načíst.  
  
 Ve scénáři, kde aplikace potřebuje pouze číst data z disku, můžete požádat, aby jí nikdy nebyla udělena žádná oprávnění k zápisu. V případě chyby nebo škodlivého útoku váš kód nemůže poškodit data, na kterých pracuje. Další informace naleznete v [tématu Žádost o oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Zabezpečení založené na rolích a CAS  
 Implementace zabezpečení založeného na rolích a zabezpečení přístupu kódu (CAS) zvyšuje celkové zabezpečení vaší aplikace. Zabezpečení založené na rolích může být založeno na účtu systému Windows nebo vlastní identitě, takže informace o objektu zabezpečení jsou k dispozici aktuálnímu vláknu. Kromě toho jsou aplikace často nutné poskytnout přístup k datům nebo prostředkům na základě pověření zadaných uživatelem. Tyto aplikace obvykle kontrolují roli uživatele a poskytují přístup k prostředkům na základě těchto rolí.  
  
 Zabezpečení založené na rolích umožňuje komponentě identifikovat aktuální uživatele a jejich přidružené role za běhu. Tyto informace jsou pak mapovány pomocí zásadcasu k určení sady oprávnění udělených za běhu. Pro zadanou doménu aplikace může hostitel změnit výchozí zásady zabezpečení založené na rolích a nastavit výchozí zaregistrovaný objekt zabezpečení, který představuje uživatele a role přidružené k tomuto uživateli.  
  
 CLR používá oprávnění k implementaci svého mechanismu pro vynucení omezení spravovaného kódu. Oprávnění zabezpečení založená na rolích poskytují mechanismus pro zjišťování, zda uživatel (nebo agent jednající jménem uživatele) má určitou identitu nebo je členem zadané role. Další informace naleznete v [tématu Oprávnění zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 V závislosti na typu aplikace, kterou vytváříte, byste měli také zvážit implementaci oprávnění založených na rolích v databázi. Další informace o zabezpečení na základě rolí na serveru SQL Server naleznete v tématu [SQL Server Security](./sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení tvoří základní jednotku nasazení, správy verzí, opakovaného použití, oboru aktivace a oprávnění zabezpečení pro aplikaci rozhraní .NET Framework. Sestavení poskytuje kolekci typů a prostředků, které jsou vytvořeny pro spolupráci a tvoří logickou jednotku funkčnosti. Clr typ neexistuje mimo kontext sestavení. Další informace o vytváření a nasazování sestavení naleznete v [tématu Programování pomocí sestavení](../../../standard/assembly/program.md).  
  
### <a name="strong-naming-assemblies"></a>Sestavení se silným pojmenováním  
 Silný název nebo digitální podpis se skládá z identity sestavení, která obsahuje jeho jednoduchý textový název, číslo verze a informace o jazykové verzi (pokud jsou k dispozici), plus veřejný klíč a digitální podpis. Digitální podpis je generován ze souboru sestavení pomocí odpovídajícího soukromého klíče. Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hashy všech souborů, které tvoří sestavení.  
  
 Silné pojmenování sestavení poskytuje aplikaci nebo součásti jedinečnou identitu, kterou může jiný software použít k explicitnímu odkazu. Silné pojmenování chrání sestavení proti falšované sestavení, které obsahuje nepřátelský kód. Silné pojmenování také zajišťuje konzistenci správy verzí mezi různými verzemi komponenty. Je nutné silné názvy sestavení, které budou nasazeny do globální mezipaměti sestavení (GAC). Další informace naleznete v [tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Částečný vztah důvěryhodnosti v ADO.NET 2.0  
 V ADO.NET 2.0 může poskytovatel dat rozhraní .NET Framework pro SQL Server, zprostředkovatel dat rozhraní .NET Framework pro technologie OLE DB, zprostředkovatel dat rozhraní .NET Framework pro rozhraní ODBC a zprostředkovatel dat rozhraní .NET Framework pro oracle nyní běžet v částečně důvěryhodných prostředích. V předchozích verzích rozhraní .NET Framework byla podporována pouze <xref:System.Data.SqlClient> v aplikacích s méně než plnou důvěryhodností.  
  
 Minimálně částečně důvěryhodné aplikace pomocí zprostředkovatele SQL <xref:System.Data.SqlClient.SqlClientPermission> Server musí mít spuštění a oprávnění.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Vlastnosti atributu oprávnění pro částečný vztah důvěryhodnosti  
 U scénářů částečnédůvěryhodnosti <xref:System.Data.SqlClient.SqlClientPermissionAttribute> můžete členy použít k dalšímu omezení funkcí dostupných pro zprostředkovatele dat rozhraní .NET Framework pro SQL Server.  
  
 V následující tabulce <xref:System.Data.SqlClient.SqlClientPermissionAttribute> jsou uvedeny dostupné vlastnosti a jejich popisy:  
  
|Vlastnost atributu Permission|Popis|  
|-----------------------------------|-----------------|  
|`Action`|Získá nebo nastaví akci zabezpečení. Zděděno z <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Povolí nebo zakáže použití prázdného hesla v připojovacím řetězci. Platné hodnoty `true` jsou (pro povolení použití prázdných hesel) a `false` (zakázat používání prázdných hesel). Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Identifikuje povolený připojovací řetězec. Lze identifikovat více připojovacích řetězců. **Poznámka:**  Do připojovacího řetězce nezahrnujte ID uživatele ani heslo. V této verzi nelze změnit omezení připojovacího řetězce pomocí nástroje konfigurace rozhraní .NET Framework. <br /><br /> Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Identifikuje parametry připojovacího řetězce, které jsou povoleny nebo zakázány. Parametry připojovacího řetězce jsou identifikovány v * \<názvu parametru*formuláře>= . Lze zadat více parametrů, které budou vymezeny pomocí středníku (;). **Poznámka:**  `KeyRestrictions`Pokud nezadáte , ale `KeyRestrictionBehavior` nastavíte vlastnost `AllowOnly` nebo `PreventUsage`, nejsou povoleny žádné další parametry připojovacího řetězce. Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identifikuje parametry připojovacího řetězce jako`AllowOnly`jediné další povolené parametry ( )`PreventUsage`nebo identifikuje další parametry, které nejsou povoleny ( . `AllowOnly` je výchozí možnost. Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Získá jedinečný identifikátor pro tento atribut při implementaci v odvozené třídě. Zděděno z <xref:System.Attribute>.|  
|`Unrestricted`|Označuje, zda je deklarováno neomezené oprávnění k prostředku. Zděděno z <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Syntaxe řetězce připojení  
 Následující příklad ukazuje, jak `connectionStrings` použít prvek konfiguračního souboru povolit pouze určitý připojovací řetězec, který má být použit. Další informace o ukládání a načítání připojovacích řetězců z konfiguračních souborů naleznete v [tématu Připojovací řetězce.](connection-strings.md)  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Syntaxe omezení klíče  
 Následující příklad umožňuje stejný připojovací řetězec, umožňuje použití možnosti `Encrypt` a `Packet Size` připojovací řetězec, ale omezuje použití jakékoli jiné možnosti připojovacího řetězce.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior s syntaxí preventusage  
 Následující příklad povolí stejný připojovací řetězec a `User Id`všechny `Password` `Persist Security Info`ostatní parametry připojení s výjimkou položek a .  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior s syntaxí AllowOnly  
 Následující příklad umožňuje dva připojovací `Connection Timeout` `Encrypt`řetězce, `Packet Size` které také obsahují `Initial Catalog`, , a parametry. Všechny ostatní parametry připojovacího řetězce jsou omezeny.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"
    connectionString="Data Source=(local);Initial
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"
    connectionString="Data Source=SqlServer2;Initial
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Povolení částečného vztahu důvěryhodnosti pomocí vlastní sady oprávnění  
 Chcete-li povolit použití <xref:System.Data.SqlClient> oprávnění pro určitou zónu, musí správce systému vytvořit vlastní sadu oprávnění a nastavit ji jako sadu oprávnění pro určitou zónu. Výchozí sady oprávnění, `LocalIntranet`například , nelze změnit. Chcete-li například zahrnout <xref:System.Data.SqlClient> oprávnění <xref:System.Security.Policy.Zone> pro `LocalIntranet`kód, který obsahuje písmeno `LocalIntranet`a ), správce systému může zkopírovat <xref:System.Data.SqlClient> sadu oprávnění pro , přejmenovat ji na "CustomLocalIntranet", přidat oprávnění, importovat `LocalIntranet_Zone` sadu oprávnění CustomLocalIntranet pomocí [nástroje Caspol.exe (Nástroj zásad zabezpečení přístupu kódu)](../../tools/caspol-exe-code-access-security-policy-tool.md)a nastavit sadu oprávnění na CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Ukázková sada oprávnění  
 Následuje ukázková sada oprávnění pro zprostředkovatele dat rozhraní .NET Framework pro SQL Server v částečně důvěryhodném scénáři. Informace o vytváření vlastních sad oprávnění naleznete v [tématu Konfigurace sad oprávnění pomocí souboru Caspol.exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Ověření přístupu ke kódu ADO.NET pomocí oprávnění zabezpečení  
 Pro scénáře částečné důvěryhodnosti můžete vyžadovat oprávnění CAS pro určité metody <xref:System.Data.SqlClient.SqlClientPermissionAttribute>v kódu zadáním . Pokud toto oprávnění není povoleno zásady zabezpečení omezené v platnosti, je vyvolána výjimka před spuštěním kódu. Další informace o zásadách zabezpečení naleznete v [tématu Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) a [doporučené postupy pro zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak psát kód, který vyžaduje konkrétní připojovací řetězec. Simuluje odepření neomezených oprávnění , <xref:System.Data.SqlClient>které by správce systému implementoval pomocí zásad cas v reálném světě.  
  
> [!IMPORTANT]
> Při navrhování cas oprávnění pro ADO.NET, správný vzor je začít s nejvíce omezující případ (žádná oprávnění vůbec) a pak přidat konkrétní oprávnění, které jsou potřebné pro konkrétní úkol, který kód potřebuje provést. Opačný vzor, počínaje všechna oprávnění a potom odepření konkrétní oprávnění, není zabezpečený, protože existuje mnoho způsobů vyjádření stejného připojovacího řetězce. Pokud například začnete se všemi oprávněními a pokusíte se odepřít použití připojovacího řetězce "server=someserver", bude stále povolen řetězec "server=someserver.mycompany.com". Tím, že vždy začíná tím, že udělí žádná oprávnění vůbec, snížíte pravděpodobnost, že jsou díry v sadě oprávnění.  
  
 Následující kód ukazuje, `SqlClient` jak provádí požadavek zabezpečení, který vyvolá, <xref:System.Security.SecurityException> pokud příslušná oprávnění CAS nejsou na místě. Výstup <xref:System.Security.SecurityException> se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Tento výstup byste měli vidět v okně konzoly:  
  
```output  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a>Interoperabilita s nespravovaným kódem  
 Kód, který běží mimo CLR se nazývá nespravovaný kód. Proto mechanismy zabezpečení, jako je například CAS nelze použít na nespravovaný kód. Komponenty modelu COM, rozhraní ActiveX a funkce rozhraní API systému Windows jsou příklady nespravovaného kódu. Zvláštní důležité informace o zabezpečení platí při provádění nespravovaného kódu, abyste neohrozili celkové zabezpečení aplikace. Další informace naleznete [v tématu Spolupráce s nespravovaným kódem](../../interop/index.md).  
  
 Rozhraní .NET Framework také podporuje zpětnou kompatibilitu s existujícími součástmi modelu COM tím, že poskytuje přístup prostřednictvím interop modelu COM. Součásti modelu COM můžete začlenit do aplikace rozhraní .NET Framework pomocí nástrojů interop modelu COM pro import příslušných typů modelu COM. Po importu jsou typy COM připraveny k použití. Interop modelu COM také umožňuje klientům COM přístup ke spravovanému kódu exportem metadat sestavení do knihovny typů a registrací spravované součásti jako součásti modelu COM. Další informace naleznete v [tématu Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [Zabezpečení v nativním a .NET Framework Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Zabezpečení na základě rolí](../../../standard/security/role-based-security.md)
- [Přehled ADO.NET](ado-net-overview.md)
