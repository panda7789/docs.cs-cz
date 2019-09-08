---
title: Zabezpečení přístupu ke kódu a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: 080432670c68623433a6b4e61adba77cf6fa5ec7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786867"
---
# <a name="code-access-security-and-adonet"></a>Zabezpečení přístupu ke kódu a ADO.NET
.NET Framework nabízí zabezpečení na základě rolí a také zabezpečení přístupu kódu (CAS), které jsou implementovány pomocí běžné infrastruktury dodávané modulem CLR (Common Language Runtime). V celém světě nespravovaného kódu je většina aplikací spouštěna s oprávněními uživatele nebo objektu zabezpečení. V důsledku toho může dojít k poškození počítačových systémů a ohrožení bezpečnosti osobních dat, když uživatel se zvýšenými oprávněními spustí škodlivý software nebo chybně vyplněný software.  
  
 Naproti tomu spravovaný kód, který je spuštěn v .NET Framework zahrnuje zabezpečení přístupu kódu, které platí pouze pro kód. Zda je povoleno spuštění kódu nebo nezávisí na původu kódu nebo jiných aspektech identity kódu, a nikoli pouze k identitě objektu zabezpečení. To snižuje pravděpodobnost, že spravovaný kód může být nepoužit.  
  
## <a name="code-access-permissions"></a>Oprávnění pro přístup kódu  
 Při spuštění kódu prezentuje důkaz, který je vyhodnocován systémem zabezpečení CLR. Tento důkaz obvykle zahrnuje původ kódu, včetně adresy URL, webu a zóny, a digitálních podpisů, které zajišťují identitu sestavení.  
  
 Modul CLR umožňuje kódu provádět pouze operace, které má kód mít oprávnění k provedení. Kód může požadovat oprávnění a tyto požadavky jsou přijaty na základě zásad zabezpečení nastavených správcem.  
  
> [!NOTE]
> Kód spuštěný v modulu CLR nemůže udělit oprávnění sám sobě. Kód může například požadovat a udělit méně oprávnění, než povoluje zásada zabezpečení, ale nikdy mu nebude uděleno více oprávnění. Při udělování oprávnění začněte bez všech oprávnění a pak přidejte užší oprávnění pro konkrétní prováděný úkol. Počínaje všemi oprávněními a pak jejich odepření vede k nezabezpečeným aplikacím, které mohou obsahovat neúmyslné bezpečnostní otvory od udělení více oprávnění, než je potřeba. Další informace najdete v tématu [Konfigurace zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7c9c2y1w(v=vs.100)) a [správy zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
 Existují tři typy oprávnění pro přístup kódu:  
  
- `Code access permissions`je odvozena <xref:System.Security.CodeAccessPermission> od třídy. Pro přístup k chráněným prostředkům, například k souborům a proměnným prostředí, a k provádění chráněných operací, jako je například přístup k nespravovanému kódu, jsou vyžadována oprávnění.  
  
- `Identity permissions`představuje vlastnosti, které identifikují sestavení. Oprávnění jsou udělena sestavení na základě legitimace, která může obsahovat položky, jako je například digitální podpis nebo kde vznikl kód. Oprávnění identity se také odvozují <xref:System.Security.CodeAccessPermission> ze základní třídy.  
  
- `Role-based security permissions`jsou založeny na tom, zda má objekt zabezpečení zadanou identitu, nebo je členem zadané role. <xref:System.Security.Permissions.PrincipalPermission> Třída umožňuje deklarativní i imperativní kontroly oprávnění vůči aktivnímu objektu zabezpečení.  
  
 Aby bylo možné zjistit, zda je kód autorizován pro přístup k prostředku nebo provedení operace, systém zabezpečení modulu runtime projde zásobník volání a porovná udělená oprávnění každého volající k oprávněním, která se vyžadují. Pokud nějaký volající v zásobníku volání nemá požadované oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka a přístup je odmítnut.  
  
### <a name="requesting-permissions"></a>Žádosti o oprávnění  
 Účelem vyžádání oprávnění je informovat modul runtime o tom, jaká oprávnění vaše aplikace vyžaduje, aby běžela a zajistila, že obdrží pouze oprávnění, která skutečně potřebují. Například pokud vaše aplikace potřebuje zapsat data na místní disk, vyžaduje <xref:System.Security.Permissions.FileIOPermission>. Pokud toto oprávnění nebylo uděleno, aplikace se při pokusu o zápis na disk nezdaří. Pokud však aplikace požaduje `FileIOPermission` a toto oprávnění nebylo uděleno, aplikace vyvolá výjimku na začátku a nebude načtena.  
  
 V případě, že aplikace potřebuje jenom číst data z disku, můžete požádat, aby nikdy nebyla udělena žádná oprávnění k zápisu. V případě chyby nebo škodlivého útoku nemůže váš kód poškodit data, na kterých funguje. Další informace najdete v tématu [vyžádání oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).  
  
## <a name="role-based-security-and-cas"></a>Zabezpečení založené na rolích a CAS  
 Implementace zabezpečení založeného na rolích i zabezpečením kódu (CAS) vylepšuje celkové zabezpečení vaší aplikace. Zabezpečení založené na rolích může být založené na účtu systému Windows nebo na vlastní identitě a zpřístupňuje informace o objektu zabezpečení, který je k dispozici pro aktuální vlákno. Kromě toho se aplikace často vyžadují k poskytnutí přístupu k datům nebo prostředkům na základě přihlašovacích údajů zadaných uživatelem. Tyto aplikace obvykle kontrolují roli uživatele a poskytují přístup k prostředkům na základě těchto rolí.  
  
 Zabezpečení na základě rolí umožňuje komponentě identifikovat aktuální uživatele a jejich přidružené role v době běhu. Tyto informace se pak namapují pomocí zásad CAS k určení sady oprávnění udělených v době běhu. U zadané domény aplikace může hostitel změnit výchozí zásady zabezpečení na základě rolí a nastavit výchozí objekt zabezpečení, který představuje uživatele a role přidružené k tomuto uživateli.  
  
 Modul CLR používá oprávnění k implementaci mechanismu pro vynucování omezení spravovaného kódu. Oprávnění zabezpečení na základě rolí poskytují mechanismus pro zjištění, zda uživatel (nebo agent jednající jménem uživatele) má konkrétní identitu nebo je členem zadané role. Další informace najdete v tématu [oprávnění zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5ba4k1c5(v=vs.100)).  
  
 V závislosti na typu aplikace, kterou sestavíte, byste měli také zvážit implementaci oprávnění na základě rolí v databázi. Další informace o zabezpečení na základě rolí v SQL Server najdete v tématu [SQL Server Security](./sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení tvoří základní jednotku nasazení, řízení verze, opětovné použití, rozsah aktivace a oprávnění zabezpečení pro .NET Framework aplikaci. Sestavení poskytuje kolekci typů a prostředků, které jsou sestaveny tak, aby spolupracovaly a tvořily logickou jednotku funkcí. Pro CLR, neexistuje typ mimo kontext sestavení. Další informace o vytváření a nasazování sestavení naleznete v tématu [programování se sestaveními](../../app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Sestavení se silným pojmenováním  
 Silný název nebo digitální podpis se skládá z identity sestavení, která zahrnuje jeho jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je k dispozici) a také veřejný klíč a digitální podpis. Digitální podpis je vygenerován ze souboru sestavení pomocí odpovídajícího privátního klíče. Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení.  
  
 Silné pojmenování sestavení dává aplikaci nebo komponentě jedinečnou identitu, kterou může jiný software použít k tomu, aby se k ní explicitně odkazoval. Silné názvy sestavení chrání proti falšování sestavením, které obsahuje nepřátelský kód. Silné pojmenovávání také zajišťuje konzistenci verzí mezi různými verzemi součásti. Je nutné, aby sestavení se silným názvem, která budou nasazena do globální mezipaměti sestavení (GAC). Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Částečná důvěryhodnost v ADO.NET 2,0  
 V ADO.NET 2,0 Zprostředkovatel dat .NET Framework pro SQL Server, .NET Framework Zprostředkovatel dat pro OLE DB, .NET Framework Zprostředkovatel dat pro rozhraní ODBC a .NET Framework Zprostředkovatel dat pro Oracle se teď dají spouštět v částečně důvěryhodných prostředích. V předchozích verzích .NET Framework byl podporován pouze <xref:System.Data.SqlClient> v aplikacích s úplným vztahem důvěryhodnosti.  
  
 Minimálně částečně důvěryhodná aplikace, která používá poskytovatele SQL Server, musí mít provádění a <xref:System.Data.SqlClient.SqlClientPermission> oprávnění.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Vlastnosti atributu oprávnění pro částečnou důvěryhodnost  
 Ve scénářích s částečnou důvěryhodností <xref:System.Data.SqlClient.SqlClientPermissionAttribute> můžete použít členy k dalšímu omezení možností dostupných pro .NET Framework Zprostředkovatel dat pro SQL Server.  
  
 V následující tabulce jsou uvedeny dostupné <xref:System.Data.SqlClient.SqlClientPermissionAttribute> vlastnosti a jejich popisy:  
  
|Vlastnost atributu oprávnění|Popis|  
|-----------------------------------|-----------------|  
|`Action`|Získá nebo nastaví akci zabezpečení. Zděděno <xref:System.Security.Permissions.SecurityAttribute>z.|  
|`AllowBlankPassword`|Povolí nebo zakáže použití prázdného hesla v připojovacím řetězci. Platné hodnoty jsou `true` (povolují použití prázdných hesel) a `false` (pro zákaz používání prázdných hesel). Zděděno <xref:System.Data.Common.DBDataPermissionAttribute>z.|  
|`ConnectionString`|Identifikuje povolený připojovací řetězec. Je možné identifikovat více připojovacích řetězců. **Poznámka:**  Do připojovacího řetězce nezahrnujte ID uživatele ani heslo. V této verzi nemůžete změnit omezení připojovacích řetězců pomocí nástroje pro konfiguraci .NET Framework. <br /><br /> Zděděno <xref:System.Data.Common.DBDataPermissionAttribute>z.|  
|`KeyRestrictions`|Identifikuje parametry připojovacího řetězce, které jsou povolené nebo zakázané. Parametry připojovacího řetězce jsou označeny v  *\<názvu parametru formuláře > =* . Lze zadat více parametrů, oddělených pomocí středníku (;). **Poznámka:**  Pokud parametr nezadáte `KeyRestrictions`, ale nastavíte `KeyRestrictionBehavior` vlastnost na `AllowOnly` nebo `PreventUsage`, nejsou povoleny žádné další parametry připojovacího řetězce. Zděděno <xref:System.Data.Common.DBDataPermissionAttribute>z.|  
|`KeyRestrictionBehavior`|Identifikuje parametry připojovacího řetězce jako pouze další povolené parametry (`AllowOnly`) nebo identifikuje další parametry, které nejsou povoleny (`PreventUsage`). `AllowOnly`je výchozí hodnota. Zděděno <xref:System.Data.Common.DBDataPermissionAttribute>z.|  
|`TypeID`|Získá jedinečný identifikátor pro tento atribut při implementaci v odvozené třídě. Zděděno <xref:System.Attribute>z.|  
|`Unrestricted`|Označuje, zda je deklarováno neomezený přístup k prostředku. Zděděno <xref:System.Security.Permissions.SecurityAttribute>z.|  
  
#### <a name="connectionstring-syntax"></a>Syntaxe ConnectionString  
 Následující příklad ukazuje, jak použít `connectionStrings` prvek konfiguračního souboru pro povolení použití pouze konkrétního připojovacího řetězce. Další informace o ukládání a načítání připojovacích řetězců z konfiguračních souborů naleznete v tématu [připojovací řetězce](connection-strings.md) .  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Syntaxe omezení počtu poplatku  
 Následující příklad povoluje stejný připojovací řetězec, umožňuje použití `Encrypt` možností a `Packet Size` připojovacího řetězce, ale omezuje použití všech dalších možností připojovacího řetězce.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior se syntaxí PreventUsage  
 Následující příklad povoluje stejný připojovací řetězec a umožňuje všechny ostatní parametry připojení s výjimkou `User Id`, `Password` a `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior se syntaxí AllowOnly  
 Následující příklad povoluje dva připojovací řetězce, `Initial Catalog`které obsahují také `Packet Size` parametry `Connection Timeout`, `Encrypt`, a. Všechny ostatní parametry připojovacího řetězce jsou omezené.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Povolení částečné důvěryhodnosti s vlastní sadou oprávnění  
 Aby bylo možné povolit používání <xref:System.Data.SqlClient> oprávnění pro konkrétní zónu, správce systému musí vytvořit vlastní sadu oprávnění a nastavit ji jako sadu oprávnění pro konkrétní zónu. Výchozí sady oprávnění, `LocalIntranet`jako například, nelze upravit. <xref:System.Data.SqlClient> Například pokud chcete zahrnout oprávnění pro kód, který <xref:System.Security.Policy.Zone> má `LocalIntranet`správce systému, může zkopírovat sadu oprávnění pro `LocalIntranet`, přejmenovat ji na "CustomLocalIntranet", přidat <xref:System.Data.SqlClient> oprávnění, importovat sada oprávnění CustomLocalIntranet nastavená pomocí [nástroje Caspol. exe (nástroj Code Access Security Policy Tool)](../../tools/caspol-exe-code-access-security-policy-tool.md)a nastavte sadu `LocalIntranet_Zone` oprávnění na CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Sada ukázkových oprávnění  
 Toto je ukázková sada oprávnění pro .NET Framework Zprostředkovatel dat pro SQL Server v částečně důvěryhodném scénáři. Informace o vytváření vlastních sad oprávnění najdete v tématu [konfigurace sad oprávnění pomocí nástroje Caspol. exe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4ybs46y6(v=vs.100)).  
  
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
 U scénářů s částečnou důvěryhodností můžete pro konkrétní metody v kódu vyžadovat oprávnění CAS zadáním <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Pokud toto oprávnění není povoleno v důsledku omezené zásady zabezpečení, je vyvolána výjimka před spuštěním kódu. Další informace o zásadách zabezpečení najdete v tématu [osvědčené postupy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100)) [pro správu zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)) a zásady zabezpečení.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak napsat kód, který vyžaduje konkrétní připojovací řetězec. Simuluje odepření neomezených oprávnění na <xref:System.Data.SqlClient>, což správce systému implementuje pomocí zásad CAS v reálném světě.  
  
> [!IMPORTANT]
> Při navrhování oprávnění CAS pro ADO.NET je správný vzor začínat s největším omezením velikosti písmen (žádná oprávnění vůbec) a pak přidat konkrétní oprávnění, která jsou potřebná pro konkrétní úkol, který kód potřebuje k provedení. Opačný vzor, počínaje všemi oprávněními a následně Odepření konkrétního oprávnění, není zabezpečený, protože existuje mnoho způsobů, jak vyjádřit stejný připojovací řetězec. Například pokud začnete se všemi oprávněními a potom se pokusíte odepřít použití připojovacího řetězce "server = someserver", řetězec "server = someserver. spolecnost. com" by byl stále povolen. Vždy, když nepovolíte žádné oprávnění, snížíte pravděpodobnost, že sada oprávnění bude mít otvory.  
  
 Následující kód demonstruje `SqlClient` , jak provádí požadavek zabezpečení, který <xref:System.Security.SecurityException> vyvolá, pokud příslušná oprávnění CAS nejsou na místě. <xref:System.Security.SecurityException> Výstup se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Tento výstup by se měl zobrazit v okně konzoly:  
  
```  
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
 Kód, který se spouští mimo modul CLR, se nazývá nespravovaný kód. Proto nelze použít mechanismy zabezpečení jako CAS pro nespravovaný kód. Mezi příklady nespravovaného kódu patří komponenty modelu COM, rozhraní ActiveX a funkce rozhraní API systému Windows. Speciální požadavky na zabezpečení platí při provádění nespravovaného kódu, takže nebudete mít v bezpečí celkové zabezpečení aplikací. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../interop/index.md).  
  
 .NET Framework také podporuje zpětnou kompatibilitu s existujícími komponentami COM tím, že poskytuje přístup prostřednictvím zprostředkovatele komunikace s objekty COM. Komponenty modelu COM lze začlenit do aplikace .NET Framework pomocí nástrojů pro spolupráci modelu COM pro import příslušných typů COM. Po importu jsou typy COM připravené k použití. Zprostředkovatel komunikace s objekty COM také umožňuje klientům modelu COM přístup k spravovanému kódu exportováním metadat sestavení do knihovny typů a registrací spravované komponenty jako komponenty modelu COM. Další informace najdete v tématu [Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [Zabezpečení v nativním a .NET Frameworkovém kódu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))
- [Zabezpečení na základě rolí](../../../standard/security/role-based-security.md)
- [Přehled ADO.NET](ado-net-overview.md)
