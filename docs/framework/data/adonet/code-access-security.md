---
title: Zabezpečení přístupu kódu a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: a608b91c78808af70bd5e9188926a12b945c5604
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453174"
---
# <a name="code-access-security-and-adonet"></a>Zabezpečení přístupu kódu a ADO.NET
Rozhraní .NET Framework poskytuje zabezpečení na základě rolí stejně jako zabezpečení přístupu kódu (CAS), které jsou implementovány pomocí společnou infrastrukturu pro zadaný modulem common language runtime (CLR). Většina aplikace na světě nespravovaného kódu jsou spouštěny s oprávnění uživatele nebo instanční objekt. V důsledku toho počítačových systémů může být poškozený a privátních dat dojde k ohrožení bezpečnosti při škodlivý nebo plný chyb softwaru je spuštěna uživatelem, se zvýšenými oprávněními.  
  
 Naopak spuštění spravovaného kódu v rozhraní .NET Framework zahrnuje zabezpečení přístupu kódu, která se vztahuje na samotný kód. Určuje, zda kód je moct spouštět, nebo není závisí na původu kódu nebo další aspekty identity kódu, nikoli jen identity objektu zabezpečení. Tím se snižuje pravděpodobnost, že spravovaná může potenciálně nebezpečného kódu.  
  
## <a name="code-access-permissions"></a>Oprávnění pro přístup kódu  
 Pokud je kód spuštěn, uvede důkaz, že se vyhodnocuje na základě systému zabezpečení CLR. Obvykle zahrnuje tohoto pověření původu kódu, včetně adres URL, lokality a zóny a digitální podpisy, které zajišťují Identita sestavení.  
  
 Modul CLR umožňuje provádět jenom operace, které kód má oprávnění k provedení. Kód můžete požádat o oprávnění, a tyto žádosti se uplatní na základě zásad zabezpečení nastavených správcem.  
  
> [!NOTE]
>  Kód spuštění v modulu CLR nelze udělit oprávnění na sebe sama. Například kód můžete vyžádat a méně oprávnění než zásady zabezpečení umožňuje, ale nikdy získá další oprávnění. Při udělování oprávnění začínat vůbec žádná oprávnění a pak přidejte nejužší oprávnění pro konkrétní úkol právě probíhá. Počínaje všechna oprávnění a pak zamítnutí jednotlivých ty vede k nezabezpečené aplikace, které mohou obsahovat neúmyslnému bezpečnostní díry poskytnout větší oprávnění než nezbytné. Další informace najdete v tématu [NIB: Konfigurace zásad zabezpečení](https://msdn.microsoft.com/library/0f130bcd-1bba-4346-b231-0bcca7dab1a4) a [NIB: Správa zásad zabezpečení](https://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
 Existují tři typy oprávnění přístupu ke kódu:  
  
-   `Code access permissions` odvozovat <xref:System.Security.CodeAccessPermission> třídy. Oprávnění se vyžadují pro přístup k chráněným prostředkům, jako jsou soubory a proměnných prostředí a k provádění chráněné operací, jako je například přístup k nespravovanému kódu.  
  
-   `Identity permissions` představuje charakteristiky, které identifikují sestavení. Oprávnění jsou udělena podle důkazy, které mohou být položky jako je například digitální podpis nebo odkud pochází kód sestavení. Oprávnění identit také provádět odvozování z <xref:System.Security.CodeAccessPermission> základní třídy.  
  
-   `Role-based security permissions` jsou založené na tom, jestli objekt zabezpečení se zadanou identitou nebo je členem zadané roli. <xref:System.Security.Permissions.PrincipalPermission> Třída umožňuje obě kontroly deklarativního a imperativního oprávnění na aktivní objekt zabezpečení.  
  
 Pokud chcete zjistit, zda kód je oprávněn přistupovat k prostředku nebo provedení operace, prochází systém zabezpečení modulu runtime zásobník volání, porovnání každého volajícího požadováné oprávnění udělená oprávnění. Pokud jakýkoli volající v zásobníku volání nemá požadované oprávnění, <xref:System.Security.SecurityException> je vyvolána a přístup je zamítnut.  
  
### <a name="requesting-permissions"></a>Vyžadování oprávnění  
 Účelem o oprávnění je informovat modul runtime oprávnění, která vaše aplikace vyžaduje, aby bylo možné spustit a ujistěte se, že bude dostávat pouze oprávnění, které skutečně potřebuje. Například pokud vaše aplikace potřebuje k zápisu dat do místního disku, vyžaduje <xref:System.Security.Permissions.FileIOPermission>. Pokud nebylo uděleno oprávnění, aplikace selže, pokud chcete zapsat na disk. Nicméně pokud aplikace požaduje `FileIOPermission` a nebylo uděleno oprávnění, vygeneruje výjimku zaměřeným na aplikaci a nenačte.  
  
 V případě, kdy aplikace potřebuje pouze ke čtení dat z disku můžete požádat, aby nikdy nebylo uděleno oprávnění pro zápis. V případě chyby nebo napadením se zlými úmysly váš kód nelze poškození dat, na kterém běží. Další informace najdete v tématu [NIB: požaduje oprávnění](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
## <a name="role-based-security-and-cas"></a>Na základě rolí zabezpečení a certifikační Autority  
 Implementace zabezpečení na základě rolí a zabezpečení zřídka kódu (CAS) zvyšuje celkovou zabezpečení pro vaši aplikaci. Na základě rolí zabezpečení může být založen na účtu Windows nebo vlastní identity, zpřístupnění informací o objektu zabezpečení pro aktuální vlákno. Aplikace jsou navíc často potřeba k poskytnutí přístupu k datům nebo prostředkům na základě přihlašovacích údajů zadaných uživatelem. Tyto aplikace obvykle zkontrolovat roli uživatele a poskytovat přístup k prostředkům na základě těchto rolí.  
  
 Zabezpečení na základě rolí umožňuje komponentě k identifikaci aktuálního uživatele a jejich přidružené role v době běhu. Tyto informace se pak namapuje pomocí zásad CAS určit sadu oprávnění udělená v době běhu. Hostitele zadané aplikační domény, můžete změnit výchozí zásady na základě rolí zabezpečení a nastavit výchozí zaregistrovaný objekt zabezpečení, představující uživatele a role přidružené k tomuto uživateli.  
  
 K implementaci jeho mechanismus pro vynucení omezení pro spravovaný kód používá modul CLR oprávnění. Oprávnění na základě role zabezpečení poskytují mechanismus pro zjištění, zda má konkrétní identitu uživatele (nebo agenta jménem uživatele), nebo je členem zadané roli. Další informace najdete v tématu [oprávnění zabezpečení](https://msdn.microsoft.com/library/b03757b4-e926-4196-b738-3733ced2bda0).  
  
 V závislosti na typu aplikace, kterou vytváříte měli byste také zvážit implementaci oprávnění na základě role v databázi. Další informace o zabezpečení na základě rolí v systému SQL Server najdete v tématu [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení tvoří základní jednotku nasazení, správu verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení pro aplikace rozhraní .NET Framework. Sestavení poskytuje kolekci typů a prostředků, které jsou vytvořené pro spolupracovaly a tvořily logickou jednotku funkčnosti. Do modulu CLR neexistuje typ mimo kontext sestavení. Další informace o vytváření a nasazování sestavení naleznete v tématu [programování se sestaveními](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Silné názvy sestavení  
 Silný název nebo digitální podpis, se skládá z identity sestavení, která zahrnuje jeho jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je poskytnuta), plus veřejného klíče a digitální podpis. Digitální podpis je vygenerován ze souboru sestavení pomocí odpovídajícího soukromého klíče. Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hash hodnoty všech souborů, které tvoří sestavení.  
  
 Silné názvy sestavení poskytuje aplikace nebo komponenty jedinečnou identitu, další software můžete na něj odkazovat explicitně. Silné názvy chrání proti se maskování podle sestavení, která obsahuje nebezpečný kód sestavení. Silné názvy také zajišťuje správu verzí konzistence mezi různými verzemi komponentu. Je třeba sestavení se silným názvem, které se nasadí do globální mezipaměti sestavení (GAC). Další informace najdete v tématu [vytvoření a použití sestavení](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Částečné důvěryhodnosti v ADO.NET 2.0  
 Ve verzi 2.0 rozhraní ADO.NET můžete zprostředkovatele dat .NET Framework pro SQL Server, zprostředkovatele dat .NET Framework pro OLE DB, zprostředkovatele dat .NET Framework pro ODBC a zprostředkovatele dat .NET Framework pro Oracle teď všechny spuštění v prostředí částečně důvěryhodné. V předchozích verzích rozhraní .NET Framework pouze <xref:System.Data.SqlClient> je podporován v méně než plně důvěryhodné aplikace.  
  
 Alespoň částečně důvěryhodné aplikace pomocí zprostředkovatele SQL Server musí mít spuštění a <xref:System.Data.SqlClient.SqlClientPermission> oprávnění.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Vlastnosti atributu oprávnění pro částečné důvěryhodnosti  
 Scénářích s částečnou důvěryhodností, můžete použít <xref:System.Data.SqlClient.SqlClientPermissionAttribute> členy k dalšímu omezit dostupné možnosti pro zprostředkovatele dat .NET Framework pro SQL Server.  
  
 V následující tabulce jsou uvedeny dostupné <xref:System.Data.SqlClient.SqlClientPermissionAttribute> vlastností a jejich popis:  
  
|Vlastnost atributu oprávnění|Popis|  
|-----------------------------------|-----------------|  
|`Action`|Získá nebo nastaví akci zabezpečení. Zděděno z <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Povolí nebo zakáže použití prázdného hesla v připojovacím řetězci. Platné hodnoty jsou `true` (Chcete-li povolit použití prázdného hesla) a `false` (Chcete-li zakázat použití prázdného hesla). Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Určuje povolené připojovací řetězec. Můžete identifikovat více připojovací řetězce. **Poznámka:** nezahrnují ID uživatele nebo heslo v připojovacím řetězci. V této verzi nelze změnit připojovací řetězec omezení pomocí konfiguračního nástroje rozhraní .NET Framework. <br /><br /> Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Identifikuje parametry připojovacího řetězce, které jsou povolené nebo zakázané. Parametry připojovacího řetězce se identifikují ve formě  *\<název parametru > =*. Lze zadat více parametrů oddělených středníkem (;). **Poznámka:** Pokud nezadáte `KeyRestrictions`, ale nastavit `KeyRestrictionBehavior` vlastnost `AllowOnly` nebo `PreventUsage`, jsou povoleny žádné další parametry připojovacího řetězce. Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identifikuje parametry připojovacího řetězce jako povolený jenom další parametry (`AllowOnly`), nebo označuje další parametry, které nejsou povoleny (`PreventUsage`). `AllowOnly` je výchozí nastavení. Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Získá jedinečný identifikátor pro tento atribut při implementaci do odvozené třídy. Zděděno z <xref:System.Attribute>.|  
|`Unrestricted`|Určuje, zda je deklarována bez omezení oprávnění k prostředku. Zděděno z <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Syntaxe připojovací řetězec  
 Následující příklad ukazuje způsob použití `connectionStrings` element konfiguračního souboru povolit pouze konkrétní připojovací řetězec má být použit. Zobrazit [připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md) Další informace o ukládání a načítání připojovacích řetězců z konfiguračních souborů.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Syntaxe KeyRestrictions  
 Následující příklad umožňuje do jednoho připojovacího řetězce, umožňuje použití `Encrypt` a `Packet Size` možnosti připojovacího řetězce, ale omezují použití žádné jiné možnosti připojovacího řetězce.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>KeyRestrictionBehavior syntaxí PreventUsage  
 Následující příklad umožňuje stejný připojovací řetězec a umožňuje všechny ostatní parametry připojení s výjimkou `User Id`, `Password` a `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>KeyRestrictionBehavior syntaxí AllowOnly  
 Následující příklad povolí dva připojovací řetězce, které také obsahují `Initial Catalog`, `Connection Timeout`, `Encrypt`, a `Packet Size` parametry. Všechny ostatní parametry připojovacího řetězce jsou omezeny.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Povolení částečném vztahu důvěryhodnosti se sadou vlastní oprávnění  
 Chcete-li povolit použití <xref:System.Data.SqlClient> oprávnění pro konkrétní zónu, může správce systému musíte vytvořit vlastní oprávnění, nastavení a nastavte ji jako sady oprávnění pro konkrétní zónu. Výchozí sady oprávnění, jako například `LocalIntranet`, nelze změnit. Například chcete zahrnout <xref:System.Data.SqlClient> oprávnění pro kód, který má <xref:System.Security.Policy.Zone> z `LocalIntranet`, zkopírovat sadu oprávnění pro správce systému `LocalIntranet`, přejmenujte ho na "CustomLocalIntranet", přidejte <xref:System.Data.SqlClient> oprávnění, import CustomLocalIntranet oprávnění nastavit pomocí [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)a nastavit oprávnění sadu `LocalIntranet_Zone` k CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Ukázková sada oprávnění  
 Tady je ukázka oprávnění nastavena pro zprostředkovatele dat .NET Framework pro SQL Server ve scénáři částečně důvěryhodné. Informace o vytváření vlastních sad oprávnění najdete v tématu [NIB: Konfigurace oprávnění nastaví pomocí Caspol.exe](https://msdn.microsoft.com/library/94e2625e-21ad-4038-af36-6d1f9df40a57).  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Ověřování pomocí oprávnění zabezpečení přístupu kódu ADO.NET  
 Pro scénáře částečné důvěryhodnosti, můžete vyžadovat, aby certifikační Autority oprávnění pro konkrétní metody v kódu tak, že zadáte <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Pokud tato oprávnění není povolena zásadami zabezpečení s omezeným přístupem v platnosti, je vyvolána výjimka, před spuštěním kódu. Další informace o zásadách zabezpečení najdete v tématu [NIB: Správa zásad zabezpečení](https://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9) a [NIB: doporučené postupy zabezpečení pro zásady](https://msdn.microsoft.com/library/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak napsat kód, který vyžaduje konkrétní připojovací řetězec. Simuluje neomezená oprávnění k odepření <xref:System.Data.SqlClient>, které správce systému může implementovat pomocí zásad CAS v reálném světě.  
  
> [!IMPORTANT]
>  Při navrhování oprávnění certifikačních Autorit pro technologii ADO.NET, správné vzor je začít s nejvíce omezující případu (bez oprávnění všechny) a pak přidejte konkrétní oprávnění, které jsou potřeba pro konkrétní úlohu, kterou je potřeba provést kód. Opačné vzor, počínaje všechna oprávnění a pak odepření konkrétní oprávnění není zabezpečené, protože existuje mnoho způsobů vyjádření do jednoho připojovacího řetězce. Například, pokud začnete se všechna oprávnění a pak se pokusíte zakázat používání připojovací řetězec "server = someserver", řetězec "server=someserver.mycompany.com" bude stále povolen. Vždy začněte tím, že žádná oprávnění uděluje vůbec snížíte pravděpodobnost, že jsou v sadě oprávnění díry.  
  
 Následující kód ukazuje, jak `SqlClient` provádí požadavek zabezpečení, který vyvolá <xref:System.Security.SecurityException> Pokud příslušná oprávnění certifikačních Autorit nejsou splněné. <xref:System.Security.SecurityException> Výstupu se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Tento výstup v okně konzoly byste měli vidět:  
  
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
  
## <a name="interoperability-with-unmanaged-code"></a>Vzájemná funkční spolupráce s nespravovaným kódem  
 Kód, který běží mimo rámec platformy CLR je volat nespravovaný kód. Proto nelze použít mechanismy zabezpečení, jako jsou certifikační Autority do nespravovaného kódu. Komponenty modelu COM, ActiveX, rozhraní a funkce rozhraní Win32 API jsou příkladem nespravovaného kódu. Při provádění nespravovaný kód tak, aby nebyl ohrozit zabezpečení aplikací platí zvláštní bezpečnostní aspekty. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md).  
  
 Rozhraní .NET Framework podporuje také zpětnou kompatibilitu pro existující komponenty modelu COM s přístupem prostřednictvím zprostředkovatele komunikace s objekty COM. Komponenty modelu COM můžete začlenit do aplikace rozhraní .NET Framework pomocí nástroje vzájemné spolupráce COM k importování odpovídajících typů modelu COM. Po importu, typy modelu COM jsou připravené k použití. Komunikace s objekty COM také umožňuje klientům modelu COM pro export metadat sestavení na knihovnu typů a registraci spravované komponenty jako součást COM přístup k spravovaného kódu. Další informace najdete v tématu [rozšířená interoperabilita modelů COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [PAVE zabezpečení v nativním a kódu rozhraní .NET Framework](https://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [Zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md)  
 [Zabezpečení na základě rolí](../../../../docs/standard/security/role-based-security.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
