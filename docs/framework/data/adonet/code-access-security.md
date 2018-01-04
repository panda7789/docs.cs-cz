---
title: "Zabezpečení přístupu kódu a ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 754c380972d79343eab83b9e862e478798218ffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="code-access-security-and-adonet"></a>Zabezpečení přístupu kódu a ADO.NET
Rozhraní .NET Framework nabízí na základě rolí zabezpečení a také zabezpečení přístupu kódu (CAS), které jsou implementovány pomocí běžnou infrastrukturu poskytl common language runtime (CLR). Na světě nespravovaného kódu většinu aplikací spustit s oprávněními uživatele nebo objekt zabezpečení. V důsledku toho počítačích může být poškozena a privátní data ohrožení zabezpečení při škodlivý nebo plný chyb softwaru je spustit uživatel, se zvýšenými oprávněními.  
  
 Naopak provádění spravovaného kódu v rozhraní .NET Framework zahrnuje zabezpečení přístupu kódu, která se vztahuje na kód samostatně. Zda kód je povoleno spuštění nebo není závisí na jeho původu a další aspekty identity kódu, ne pouze identita objektu zabezpečení. Tím se snižuje pravděpodobnost, že spravované můžete došlo ke zneužití kódu.  
  
## <a name="code-access-permissions"></a>Oprávnění pro přístup kódu  
 Pokud je kód spuštěn, uvede důkaz, který se vyhodnotí v systému zabezpečení CLR. Tento důkaz obvykle zahrnuje původ kód, včetně adres URL, lokality a zóny a digitální podpisy, které zajišťují identitu sestavení.  
  
 Modul CLR umožňuje provádět jenom operace, které kód má oprávnění k provedení. Kód můžete požádat o oprávnění a tyto požadavky se uplatní na základě zásad zabezpečení nastavenou správcem.  
  
> [!NOTE]
>  Kód v modulu CLR nelze udělit oprávnění na sebe sama. Například kód může požádat o a udělit méně oprávnění, než povoluje zásadu zabezpečení, ale bude nikdy nebylo uděleno další oprávnění. Při udělování oprávnění, začínat vůbec žádná oprávnění a poté přidejte nejbližší oprávnění pro provedení úkolu během provádění. Počínaje všechna oprávnění a potom odepření jednotlivých ty vede k nezabezpečené aplikace, které mohou obsahovat neúmyslnému celistvosti z udělení větší oprávnění než nezbytné. Další informace najdete v tématu [NIB: Konfigurace zásad zabezpečení](http://msdn.microsoft.com/en-us/0f130bcd-1bba-4346-b231-0bcca7dab1a4) a [NIB: Správa zásad zabezpečení](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
 Existují tři typy kódu přístupová oprávnění:  
  
-   `Code access permissions`odvozena od <xref:System.Security.CodeAccessPermission> třídy. Oprávnění se vyžadují, aby bylo možné přístup k chráněným prostředkům, jako jsou soubory a proměnné prostředí a k provádění chráněné operace, jako je přístup k nespravovanému kódu.  
  
-   `Identity permissions`představuje charakteristiky, které identifikují sestavení. Oprávnění k sestavení založené na důkaz, které mohou být položky, jako je například digitální podpis nebo odkud pochází kód. Oprávnění identity také odvodit z <xref:System.Security.CodeAccessPermission> základní třídy.  
  
-   `Role-based security permissions`jsou založené na tom, jestli objekt se zadanou identitou nebo je členem zadané roli. <xref:System.Security.Permissions.PrincipalPermission> Třída umožňuje obou kontroly deklarativní a imperativní oprávnění vůči aktivní objekt zabezpečení.  
  
 K určení, zda kód je oprávněn k přístupu k prostředkům nebo k provedení operace, systém zabezpečení modulu runtime prochází zásobník volání, porovnává udělená oprávnění jednotlivých volajícího, aby požadováné. Pokud žádné volající v zásobníku volání nemá požadované oprávnění, <xref:System.Security.SecurityException> je vyvolána a přístup je zamítnut.  
  
### <a name="requesting-permissions"></a>Vyžadování oprávnění  
 Účelem vyžádání oprávnění je informovat runtime oprávnění, která vaše aplikace vyžaduje, aby bylo možné spustit a ujistěte se, že dostal pouze oprávnění, která ve skutečnosti potřebuje. Například pokud aplikace potřebuje k zápisu dat do místního disku, vyžaduje <xref:System.Security.Permissions.FileIOPermission>. Pokud tato oprávnění nebylo uděleno, aplikace se nezdaří, při pokusu o zápis na disk. Ale pokud aplikace požádá o `FileIOPermission` a že nebylo uděleno oprávnění, aplikace vygeneruje výjimku na začátku a nenačte se.  
  
 Ve scénáři, kde aplikace potřebuje pouze ke čtení dat z disku můžete požádat, aby nikdy nebylo uděleno žádné oprávnění k zápisu. V případě chyby nebo napadením se zlými úmysly nelze kódu dojít k poškození dat, na kterých pracuje. Další informace najdete v tématu [NIB: požaduje oprávnění](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
## <a name="role-based-security-and-cas"></a>Na základě rolí zabezpečení a certifikačních Autorit  
 Implementace na základě rolí zabezpečení a zabezpečení získat přístup k kódu (CAS) zvyšuje celkové zabezpečení pro vaši aplikaci. Na základě rolí zabezpečení, může být založen na účet systému Windows nebo vlastní identity, zpřístupnění informací o objekt zabezpečení pro aktuální vlákno. Aplikace jsou navíc často potřeba k poskytování přístupu k datům nebo prostředky v závislosti na přihlašovací údaje zadané uživatelem. Tyto aplikace obvykle zkontrolujte roli uživatele a poskytovat přístup k prostředkům na základě těchto rolí.  
  
 Zabezpečení na základě rolí umožňuje komponentu k identifikaci aktuálního uživatele a jejich přidružené role v době běhu. Tyto informace pak je namapovaný k určení sady oprávnění udělená v době běhu pomocí certifikační Autority zásad. Hostitel pro zadanou aplikaci doménu, můžete změnit výchozí zásady na základě rolí zabezpečení a nastavit objekt zabezpečení výchozí, který reprezentuje uživatele a role související s tímto uživatelem.  
  
 Modul CLR používá oprávnění k implementaci jeho mechanismus pro vynucení omezení spravovaného kódu. Oprávnění na základě role zabezpečení poskytují mechanismus pro zjištění, zda má zvláštní identitu uživatele (nebo agenta jménem uživatele), nebo je členem zadané roli. Další informace najdete v tématu [oprávnění zabezpečení](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0).  
  
 V závislosti na typu aplikace, kterou vytváříte měli byste také zvážit implementace oprávnění na základě rolí v databázi. Další informace o zabezpečení na základě rolí v systému SQL Server najdete v tématu [zabezpečení SQL serveru](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení vytváří základní jednotku nasazení, Správa verzí, opakované použití, aktivaci oborů a oprávnění zabezpečení pro aplikace .NET Framework. Sestavení poskytuje kolekci typů a prostředků, které jsou vytvořeny a společně tvoří logickou jednotku funkčnosti. Modulu CLR typu neexistuje mimo kontext sestavení. Další informace o vytvoření a nasazení sestavení najdete v tématu [programování se sestaveními](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Silné názvy sestavení  
 Silný název nebo digitální podpis, se skládá z identity sestavení, která zahrnuje jeho jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je zadáno), plus veřejný klíč a digitální podpis. Digitální podpis je generována ze souboru sestavení pomocí odpovídajícího privátního klíče. Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení.  
  
 Silné názvy sestavení poskytuje aplikaci nebo součásti, na ostatní software můžete na ni odkazuje explicitně jedinečnou identitu. Silné názvy chrání sestavení proti se sestavením, který obsahuje kód k tomuto účelu maskování. Silné názvy zajišťuje správu verzí konzistence mezi různými verzemi součásti. Je nutné v sestavení se silným názvem, které se nasadí do globální mezipaměti sestavení (GAC). Další informace najdete v tématu [vytvoření a použití sestavení](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Částečná důvěryhodnost v ADO.NET 2.0  
 V ADO.NET 2.0 můžete zprostředkovatele dat .NET Framework pro SQL Server, zprostředkovatel dat .NET Framework pro OLE DB, zprostředkovatel dat .NET Framework pro ODBC a zprostředkovatel dat .NET Framework pro Oracle nyní ve všech spuštění částečně důvěryhodného prostředí. V předchozích verzích rozhraní .NET Framework, pouze <xref:System.Data.SqlClient> byl podporován v aplikacích menší než plné důvěryhodnosti.  
  
 Minimálně, částečně důvěryhodné aplikace pomocí zprostředkovatele SQL Server musí mít provádění a <xref:System.Data.SqlClient.SqlClientPermission> oprávnění.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Vlastnosti atributu oprávnění pro částečné důvěryhodnosti  
 Scénáře částečné důvěryhodnosti, můžete použít <xref:System.Data.SqlClient.SqlClientPermissionAttribute> členy k dalšímu omezení možnosti dostupné pro zprostředkovatele dat .NET Framework pro SQL Server.  
  
 Následující tabulka uvádí dostupných <xref:System.Data.SqlClient.SqlClientPermissionAttribute> vlastnosti a jejich popisy:  
  
|Vlastnost atributu oprávnění|Popis|  
|-----------------------------------|-----------------|  
|`Action`|Získá nebo nastaví akci zabezpečení. Zděděno z <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Povolí nebo zakáže použití prázdné heslo v připojovacím řetězci. Platné hodnoty jsou `true` (Chcete-li povolit použití prázdného hesla) a `false` (Chcete-li zakázat používání prázdná hesla). Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Identifikuje povolených připojovací řetězec. Je možné zjistit více připojovací řetězce. **Poznámka:** nezahrnují ID uživatele nebo heslo v připojovacím řetězci. V této verzi nelze změnit pomocí nástroje rozhraní .NET Framework konfigurace omezení řetězec připojení. <br /><br /> Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Určuje parametry připojovacího řetězce, které jsou povolené nebo zakázané. Ve formuláři jsou identifikovány parametrů řetězce připojení  *\<název parametru > =*. Můžete zadat víc parametrů oddělený středníkem (;). **Poznámka:** Pokud nezadáte `KeyRestrictions`, ale nastavit `KeyRestrictionBehavior` vlastnost `AllowOnly` nebo `PreventUsage`, jsou povolené žádné další parametry připojovacího řetězce. Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identifikuje parametry, řetězec připojení jako pouze další parametry, které jsou povoleny (`AllowOnly`), nebo identifikuje další parametry, které nejsou povoleny (`PreventUsage`). `AllowOnly`je výchozí. Zděděno z <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Získá jedinečný identifikátor pro tento atribut při implementaci v odvozené třídě. Zděděno z <xref:System.Attribute>.|  
|`Unrestricted`|Určuje, zda je deklarovaná bez omezení oprávnění k prostředku. Zděděno z <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Syntaxe připojovacího řetězce  
 Následující příklad ukazuje, jak používat `connectionStrings` prvek konfiguračního souboru povolit pouze konkrétní připojovací řetězec má být použit. V tématu [připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md) Další informace o ukládání a načítání připojovací řetězce z konfiguračních souborů.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Syntaxe KeyRestrictions  
 Následující příklad povolí stejný připojovací řetězec, umožňuje použití `Encrypt` a `Packet``Size` možnosti připojovací řetězec, ale omezuje použití další možnosti připojovací řetězec.  
  
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
 Následující příklad povolí stejný připojovací řetězec a umožňuje všech dalších parametrů připojení s výjimkou `User Id`, `Password` a `Persist Security Info`.  
  
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
 Následující příklad povolí dva připojovací řetězce, které také obsahují `Initial Catalog`, `Connection Timeout`, `Encrypt`, a `Packet Size` parametry. Jsou všechny ostatní parametry řetězce připojení s omezeným přístupem.  
  
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
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Povolení částečný vztah důvěryhodnosti s vlastní sady oprávnění  
 Chcete-li povolit použití <xref:System.Data.SqlClient> oprávnění pro konkrétní zónu, správce systému musí vytvořit vlastní oprávnění nastavená a nastavte jej jako oprávnění nastavené pro konkrétní zónu. Výchozí sady oprávnění, jako například `LocalIntranet`, nemůže být upraven. Například obsahovat <xref:System.Data.SqlClient> oprávnění pro kód, který má <xref:System.Security.Policy.Zone> z `LocalIntranet`, správce systému může zkopírovat sadu oprávnění pro `LocalIntranet`, přejmenujte jej na "CustomLocalIntranet", přidejte <xref:System.Data.SqlClient> oprávnění, import oprávnění CustomLocalIntranet nastavit pomocí [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)a nastavte oprávnění sadu `LocalIntranet_Zone` k CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Ukázkové sady oprávnění  
 Zde je ukázka oprávnění nastavená pro zprostředkovatele dat .NET Framework pro SQL Server ve scénáři částečně důvěryhodné. Informace o vytváření vlastních sad oprávnění najdete v tématu [NIB: Konfigurace oprávnění nastaví pomocí Caspol.exe](http://msdn.microsoft.com/en-us/94e2625e-21ad-4038-af36-6d1f9df40a57).  
  
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
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Ověřování pomocí oprávnění zabezpečení přístupu kódu technologie ADO.NET  
 U scénářů s částečným vztahem důvěryhodnosti můžete vyžadovat oprávnění certifikačních Autorit pro konkrétní metody ve vašem kódu zadáním <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Pokud tohoto oprávnění není povoleno platí zásady zabezpečení s omezeným přístupem, je vyvolána výjimka, před spuštěním kódu. Další informace o zásady zabezpečení najdete v tématu [NIB: Správa zásad zabezpečení](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9) a [NIB: osvědčené postupy zabezpečení zásady](http://msdn.microsoft.com/en-us/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak napsat kód, který vyžaduje konkrétní připojovací řetězec. Simuluje odepření neomezená oprávnění k <xref:System.Data.SqlClient>, který správce systému byste implementovat pomocí zásad certifikační Autority v reálném světě.  
  
> [!IMPORTANT]
>  Při navrhování CAS oprávnění pro technologii ADO.NET, je správné vzor začínat nejvíc omezující případ (žádná oprávnění na všechny) a potom přidat konkrétní oprávnění, které jsou potřeba pro konkrétní úkol, který potřebuje provést kód. Opačné vzor, počínaje všechna oprávnění a potom odepření konkrétní oprávnění není bezpečné, protože existuje mnoho způsobů vyjádření stejný připojovací řetězec. Například, pokud začínat všechna oprávnění a pak se pokusíte zakázat používání připojovací řetězec "serveru = someserver", bude mít možnost stále řetězec "server=someserver.mycompany.com". Vždy spuštěním udělením vůbec žádné oprávnění snížit pravděpodobnost, že jsou v sadě oprávnění díry.  
  
 Následující kód ukazuje, jak `SqlClient` provede požadavek zabezpečení, která vyvolává <xref:System.Security.SecurityException> Pokud příslušná oprávnění certifikačních Autorit nejsou na místě. <xref:System.Security.SecurityException> Výstupu se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Měli byste vidět tento výstup v okně konzoly:  
  
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
  
## <a name="interoperability-with-unmanaged-code"></a>Vzájemná funkční spolupráce pomocí nespravovaného kódu  
 Kód, který je spuštěn mimo modulu CLR je volat nespravovaný kód. Mechanismy zabezpečení, jako jsou certifikační Autority tedy nelze použít na nespravovaný kód. COM – součásti ActiveX rozhraní a funkcí rozhraní API Win32 jsou příklady nespravovaného kódu. Aspekty zabezpečení speciální platí při provádění nespravovaného kódu tak, aby není ohrozit zabezpečení celkové aplikací. Další informace najdete v tématu [spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md).  
  
 Zpětná kompatibilita na existující COM – součásti rozhraní .NET Framework také podporuje tím, že poskytuje přístup pomocí zprostředkovatele komunikace s objekty COM. COM – součásti můžete začlenit do aplikace rozhraní .NET Framework importovat relevantní typy modelu COM pomocí nástrojů zprostředkovatele komunikace s objekty COM. Po importu, typy modelu COM jsou připravené k použití. Zprostředkovatel komunikace s objekty COM také umožňuje klientům COM přístup spravovaného kódu export metadata sestavení do knihovny typů a registrací spravované součásti jako komponenty modelu COM. Další informace najdete v tématu [Advanced interoperabilita modelů COM](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Připravte si kód pro rozhraní .NET Framework a zabezpečení v nativním režimu](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)  
 [Zabezpečení přístupu kódu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)  
 [Zabezpečení na základě rolí](http://msdn.microsoft.com/en-us/239442e3-5be4-4203-b7fd-793baffea803)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
