---
title: Izolované úložiště
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data storage using isolated storage
- stores
- storing data using isolated storage
- isolated storage
- location of isolated storage in file system
- standardizing storage systems
- storing data using isolated storage, when not to use
- code, isolated storage
- isolated storage, options
- data storage using isolated storage, when not to use
- storing data using isolated storage, options
- isolated storage, when not to use
- data storage using isolated storage, options
- isolation
ms.assetid: aff939d7-9e49-46f2-a8cd-938d3020e94e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94d435d8f50683c24e7ca28100fbf5abf0fdcc19
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204781"
---
# <a name="isolated-storage"></a>Izolované úložiště
<a name="top"></a> For desktop apps, isolated storage is a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data. Standardizace poskytuje také další výhody. Správci mohou používat nástroje, které jsou navrženy pro manipulaci izolovaného úložiště, a nakonfigurovat kapacitu úložiště souborů, nastavit zásady zabezpečení a odstranit nepoužívaná data. Díky izolovanému úložišti váš kód pro zadání bezpečných umístění v systému souborů již nevyžaduje jedinečné cesty a data jsou chráněna před ostatními aplikacemi, které mají přístup pouze k izolovanému úložišti. Pevně zakódovaná informace, která označuje oblast umístění aplikace, není vyžadována.

> [!IMPORTANT]
> Isolated storage is not available for Windows 8.x Store apps. Instead, use the application data classes in the `Windows.Storage` namespaces included in the Windows Runtime API to store local data and files. For more information, see [Application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) in the Windows Dev Center.

Toto téma obsahuje následující oddíly:

- [Data Compartments and Stores](#data_compartments_and_stores)

- [Quotas for Isolated Storage](#quotas)

- [Secure Access](#secure_access)

- [Allowed Usage and Security Risks](#allowed_usage)

- [Isolated Storage Locations](#isolated_storage_locations)

- [Creating, Enumerating, and Deleting Isolated Storage](#isolated_storage_tasks)

- [Scenarios for Isolated Storage](#scenarios_for_isolated_storage)

- [Related Topics](#related_topics)

- [Reference](#reference)

<a name="data_compartments_and_stores"></a>

## <a name="data-compartments-and-stores"></a>Datové přihrádky a úložiště dat

Pokud aplikace ukládá data do souboru, je nutné pečlivě zvolit název souboru a umístění úložiště, a to za účelem minimalizace možnosti, že toto umístění úložiště bude známo také jiné aplikaci, což může způsobit náchylnost k poškození. Bez standardního systému pro řešení těchto problémů může být vývoj ad hoc technik minimalizujících konflikty úložiště složitý a výsledky nemusí být nespolehlivé.

V případě izolovaného úložiště jsou data vždy izolována podle uživatele a podle sestavení. Pověření, jako je například původ nebo silný název sestavení, určují identitu sestavení. Data mohou být izolována také podle domény aplikace pomocí obdobných pověření.

Používáte-li izolované úložiště, aplikace uloží data do jedinečné datové přihrádky, která je přidružena k některým aspektům identity kódu, jako je vydavatel nebo signatura. Datová přihrádka je abstrakcí, nikoli specifickým umístěním úložiště. Sestává z jednoho nebo více souborů izolovaného úložiště, které se nazývají „úložiště“, jež obsahují umístění skutečného adresáře, ve kterém jsou data uložena. Aplikace může mít například přidruženou datovou přihrádku a adresář v systému souborů může implementovat úložiště, které uchovává skutečná data pro aplikaci. Data uložená v úložišti mohou být libovolného druhu, od informací o uživatelských předvolbách až po stav aplikace. Pro vývojáře je umístění datové přihrádky transparentní. Úložiště se většinou nachází na straně klienta, serverová aplikace však může využívat izolovaná úložiště k ukládání informací zosobňováním uživatele, jehož jménem funguje. Izolované úložiště může také ukládat informace na serveru s cestovním profilem uživatele, aby se informace mohly přesouvat spolu s uživatelem, který je na cestách.

<a name="quotas"></a>

## <a name="quotas-for-isolated-storage"></a>Kvóty pro izolované úložiště

Kvóta je limit využívané velikosti izolovaného úložiště. Kvóta úložiště zahrnuje bajty prostoru pro soubory a také informace o režijních nákladech spojených s adresářem a další informace. Isolated storage uses permission quotas, which are storage limits that are set by using <xref:System.Security.Permissions.IsolatedStoragePermission> objects. If you try to write data that exceeds the quota, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.  Zásady zabezpečení, které lze upravit pomocí konfiguračního nástroje rozhraní .NET Framework (Mscorcfg.msc), určují, která oprávnění jsou kódu udělována. Code that has been granted <xref:System.Security.Permissions.IsolatedStoragePermission> is restricted to using no more storage than the <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A> property allows. Avšak vzhledem k tomu, že kód může obejít kvóty oprávnění předložením identity jiného uživatele, slouží kvóty oprávnění jako pokyny pro chování kódu, nikoli jako pevně stanovené omezení chování kódu.

V případě cestovních úložišť nejsou kvóty vynucovány. Chcete-li je použít, je potřeba z tohoto důvodu použít mírně vyšší stupeň oprávnění pro kód. The enumeration values <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> and <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> specify a permission to use isolated storage for a roaming user.

<a name="secure_access"></a>

## <a name="secure-access"></a>Bezpečný přístup

Používání izolovaného úložiště umožňuje částečně důvěryhodným aplikacím ukládat data způsobem, který je řízen zásadami zabezpečení počítače. Tato možnost je vhodná především pro stažené komponenty, které by měl uživatel spouštět s rozvahou. Zásady zabezpečení zřídka udělí tento druh oprávnění kódu pro přístup k systému souborů pomocí standardních vstupně-výstupních mechanismů. Ve výchozím nastavení je však oprávnění k používání izolovaného úložiště uděleno kódu, který se spouští z místního počítače, místní sítě nebo z Internetu.

Správci mohou stanovit omezení kapacity izolovaného úložiště pro aplikaci nebo uživatele, a to na základě příslušné úrovně důvěryhodnosti. Dále mohou správci kompletně odebrat trvalá data uživatele. To create or access isolated storage, code must be granted the appropriate <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission.

Chcete-li získat přístup k izolovanému úložišti, musí být kódu přidělena veškerá oprávnění pro operační systém nativní platformy. Musí být splněny podmínky seznamů řízení přístupu (ACL), jež ověřují, kteří uživatelé mají oprávnění použít systém souborů. Aplikace rozhraní .NET framework již mají oprávnění operačního systému pro přístup k izolovanému úložišti, pokud však neprovedou zosobnění (specifické pro platformu). V tomto případě musí aplikace zajistit, aby identita zosobněného uživatele měla příslušná oprávnění pro přístup k izolovanému úložišti. Tento přístup poskytuje kódu spuštěnému nebo staženému z webu čtení a zápis do oblasti úložiště vztahujícího se ke konkrétnímu uživateli.

To control access to isolated storage, the common language runtime uses <xref:System.Security.Permissions.IsolatedStorageFilePermission> objects. Jednotlivé objekty mají vlastnosti, které určují následující hodnoty:

- Povolené využití, které označuje typ povoleného přístupu. The values are members of the <xref:System.Security.Permissions.IsolatedStorageContainment> enumeration. Další informace o těchto hodnotách naleznete v tabulce v další části.

- Kvóta úložiště, která byla popsána v předchozím oddílu.

The runtime demands <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission when code first attempts to open a store. It decides whether to grant this permission, based on how much the code is trusted. If the permission is granted, the allowed usage and storage quota values are determined by security policy and by the code's request for <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Zásada zabezpečení je nastavena pomocí konfiguračního nástroje rozhraní .NET Framework (Mscorcfg.msc). Aby měli jednotliví volající alespoň povolené využití, jsou ověřování všichni volající v zásobníku volání. Modul runtime ověřuje také kvóty zadané do kódu, který otevřel nebo vytvořil úložiště, ve kterém má být soubor uložen. Pokud jsou tyto podmínky splněny, je povolení uděleno. Kvóta se ověřuje znovu pokaždé, když je soubor zapsán do úložiště.

Application code is not required to request permission because the common language runtime will grant whatever <xref:System.Security.Permissions.IsolatedStorageFilePermission> is appropriate based on security policy. However, there are good reasons to request specific permissions that your application needs, including <xref:System.Security.Permissions.IsolatedStorageFilePermission>.

<a name="allowed_usage"></a>

## <a name="allowed-usage-and-security-risks"></a>Povolené využití a rizika zabezpečení

The allowed usage specified by <xref:System.Security.Permissions.IsolatedStorageFilePermission> determines the degree to which code will be allowed to create and use isolated storage. Následující tabulka znázorňuje, jakým způsobem povolené využití zadané v rámci oprávnění odpovídá typům izolace, a podává přehled rizik zabezpečení spojených s jednotlivými typy povoleného využití.

|Povolené využití|Typy izolace|Dopad na zabezpečení|
|-------------------|---------------------|---------------------|
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Není povoleno žádné použití izolovaného úložiště.|Neexistuje žádný dopad na zabezpečení.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Izolace podle uživatele, domény a sestavení. Každé sestavení má samostatné dílčí úložiště v rámci domény. Úložiště používající toto oprávnění jsou také implicitně izolována počítačem.|Tato úroveň oprávnění ponechává prostředky otevřené neoprávněnému nadměrnému využití, ačkoli vynucené kvóty toto znesnadňují. Mluvíme o útoku na dostupnost služby (DOS).|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|Same as `DomainIsolationByUser`, but store is saved to a location that will roam if roaming user profiles are enabled and quotas are not enforced.|Vzhledem k tomu, že kvóty musí být zakázány, úložiště prostředků jsou zranitelnější vůči útokům na dostupnost služby (DOS).|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Izolace podle uživatele a sestavení. Úložiště používající toto oprávnění jsou také implicitně izolována počítačem.|Kvóty jsou na této úrovni vynuceny za účelem zamezení útoku na dostupnost služby (DOS). Možnost přístupu k tomuto úložišti stejným sestavením z jiné domény otevírá možnost úniku informací mezi aplikacemi.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|Same as `AssemblyIsolationByUser`, but store is saved to a location that will roam if roaming user profiles are enabled and quotas are not enforced.|Same as in `AssemblyIsolationByUser`, but without quotas, the risk of a denial of service attack increases.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Izolace podle uživatele. Tuto úroveň oprávnění používají obvykle pouze nástroje pro správu a ladění.|Přístup s tímto oprávněním umožňuje kódu zobrazit nebo odstranit jakýkoli soubor nebo adresář v izolovaném úložišti uživatele (bez ohledu na izolaci sestavení). Mezi rizika patří mimo jiné únik informací a ztráta dat.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Izolace podle všech uživatelů, domén a sestavení. Tuto úroveň oprávnění používají obvykle pouze nástroje pro správu a ladění.|Toto oprávnění vytváří potenciál pro celkové vyzrazení veškerých izolovaných úložišť všech uživatelů.|

<a name="isolated_storage_locations"></a>

## <a name="isolated-storage-locations"></a>Umístění izolovaného úložiště

Někdy je vhodné ověřit změnu izolovaného úložiště pomocí systému souborů operačního systému. Budete pravděpodobně chtít znát umístění souborů izolovaného úložiště. Toto umístění se liší v závislosti na operačním systému. V následující tabulce jsou uvedeny kořenové adresáře, ve kterých je izolované úložiště vytvořeno v několika běžných operačních systémech. Hledejte v tomto kořenovém adresáři adresáře Microsoft\IsolatedStorage. Chcete-li izolované úložiště zobrazit v systému souborů, musíte změnit nastavení složek tak, aby se zobrazovaly skryté soubory a složky.

|Operační systém|Umístění v systému souborů|
|----------------------|-----------------------------|
|Windows 2000, Windows XP, Windows Server 2003 (upgrade z Windows NT 4.0)|Úložiště podporující cestovní profily =<br /><br /> \<SYSTEMROOT>\Profiles\\<user\>\Application Data<br /><br /> Úložiště bez možnosti cestovního profilu =<br /><br /> \<SYSTEMROOT>\Profiles\\<user\>\Local Settings\Application Data|
|Windows 2000 – čistá instalace (a upgrady ze systému Windows 98 a Windows NT 3.51)|Úložiště podporující cestovní profily =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Application Data<br /><br /> Úložiště bez možnosti cestovního profilu =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Local Settings\Application Data|
|Windows XP, Windows Server 2003 – čistá instalace (a upgrady ze systému Windows 2000 a Windows 98)|Úložiště podporující cestovní profily =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Application Data<br /><br /> Úložiště bez možnosti cestovního profilu =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Local Settings\Application Data|
|[!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7, Windows Server 2008, Windows Vista|Úložiště podporující cestovní profily =<br /><br /> \<SYSTEMDRIVE>\Users\\<user\>\AppData\Roaming<br /><br /> Úložiště bez možnosti cestovního profilu =<br /><br /> \<SYSTEMDRIVE>\Users\\<user\>\AppData\Local|

<a name="isolated_storage_tasks"></a>

## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Vytváření, provádění výčtů a odstraňování izolovaného úložiště

The .NET Framework provides three classes in the <xref:System.IO.IsolatedStorage> namespace to help you perform tasks that involve isolated storage:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, derives from <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> and provides basic management of stored assembly and application files. An instance of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class represents a single store located in the file system.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> derives from <xref:System.IO.FileStream?displayProperty=nameWithType> and provides access to the files in a store.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope> is an enumeration that enables you to create and select a store with the appropriate isolation type.

Třídy izolovaného úložiště umožňují vytvořit, provádět výčty a odstranit izolované úložiště. The methods for performing these tasks are available through the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object. Some operations require you to have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that represents the right to administer isolated storage; you might also need to have operating system rights to access the file or directory.

For a series of examples that demonstrate common isolated storage tasks, see the how-to topics listed in [Related Topics](#related_topics).

<a name="scenarios_for_isolated_storage"></a>

## <a name="scenarios-for-isolated-storage"></a>Scénáře pro izolované úložiště

Izolované úložiště lze využít v mnoha situacích, mezi které patří tyto čtyři scénáře:

- Stažené ovládací prvky. Ovládací prvky spravovaného kódu stažené z Internetu nemohou zapisovat na pevný disk pomocí běžných vstupně-výstupních tříd, mohou však používat izolované úložiště pro uchování uživatelských nastavení a stavů aplikace.

- Úložiště sdílených komponent. Komponenty sdílené mezi aplikacemi mohou používat izolované úložiště pro poskytování řízeného přístupu k úložišti dat.

- Serverové úložiště. Serverové aplikace mohou používat izolované úložiště pro poskytování individuálních úložišť pro velký počet uživatelů, kteří vytvářejí požadavky na aplikaci. Vzhledem k tomu, že izolované úložiště je vždy odděleno od uživatele, musí server zosobnit uživatele, který vytváří daný požadavek. In this case, data is isolated based on the identity of the principal, which is the same identity the application uses to distinguish between its users.

- Cestovní profily. Aplikace mohou izolované úložiště používat také s cestovními profily uživatelů. Díky tomu se mohou izolovaná úložiště přesouvat spolu s profilem.

Izolované úložiště byste neměli používat v následujících situacích:

- Pro ukládání vysoce citlivých údajů, jako jsou například nezašifrované klíče nebo hesla, protože izolované úložiště není chráněno před vysoce důvěryhodným kódem, nespravovaným kódem nebo před důvěryhodnými uživateli počítače.

- Pro uložení kódu.

- Pro uložení nastavení konfigurace a nasazení, které řídí správci. (Předvolby uživatele se nepovažují za nastavení konfigurace, protože je správci neovládají.)

Mnoho aplikací používá databáze k ukládání a izolaci dat. V tomto případě jeden nebo více řádků v databázi může představovat úložiště pro konkrétního uživatele. Můžete se rozhodnout pro používání izolovaného úložiště namísto databáze, pokud je počet uživatelů nízký, pokud je režie používání databáze značná, nebo pokud neexistuje žádné zařízení pro databázi. Také pokud aplikace vyžaduje úložiště, které je pružnější a složitější než možnosti řádku v databázi. Izolované úložiště může poskytnout reálnou alternativu.

<a name="related_topics"></a>

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Typy izolace](../../../docs/standard/io/types-of-isolation.md)|Popisuje různé typy izolace.|
|[Postupy: Získávání úložišť pro izolované úložiště](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|Provides an example of using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class to obtain a store isolated by user and assembly.|
|[Postupy: Vytvoření výčtu úložišť pro izolované úložiště](../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|Shows how to use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> method to calculate the size of all isolated storage for the user.|
|[Postupy: Odstraňování úložišť v izolovaném úložišti](../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|Shows how to use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> method in two different ways to delete isolated stores.|
|[Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště](../../../docs/standard/io/how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Zobrazuje způsob měření zbývající kapacity v izolovaném úložišti.|
|[Postupy: Vytváření souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|Obsahuje některé příklady vytváření souborů a adresářů v izolovaném úložišti.|
|[Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|Znázorňuje způsob čtení struktury adresářů a souborů v izolovaném úložišti.|
|[Postupy: Čtení a zápis do souborů v izolovaném úložišti](../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|Poskytuje příklad zápisu řetězce do souboru izolovaného úložiště a jeho zpětné čtení.|
|[Postupy: Odstraňování souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|Znázorňuje způsob odstraňování souborů a adresářů izolovaného úložiště.|
|[Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)|Objasňuje způsob vytváření synchronního a asynchronního přístupu k datovým proudům souborů a dat.|

<a name="reference"></a>

## <a name="reference"></a>Odkaz

- <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
