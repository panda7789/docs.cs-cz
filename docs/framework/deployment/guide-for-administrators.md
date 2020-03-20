---
title: .NET Framework – průvodce nasazením pro administrátory
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: be15ce0b0bed37da6fe400e98bfdd118c48f7ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716529"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework – průvodce nasazením pro administrátory

Tento podrobný článek popisuje, jak může správce systému nasadit rozhraní .NET Framework 4.5 a jeho systémové závislosti v síti pomocí nástroje Microsoft Endpoint Configuration Manager. V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework. Seznam požadavků na software a hardware pro instalaci rozhraní .NET Framework 4.5 naleznete v [tématu Systémové požadavky](../get-started/system-requirements.md).

> [!NOTE]
> Software odkazovaný v tomto dokumentu, včetně, ale bez omezení, rozhraní .NET Framework 4.5, Configuration Manager a Active Directory, podléhá licenčním podmínkám. V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je. Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.
>
> Informace o podpoře rozhraní .NET Framework naleznete v [tématu zásady oficiální podpory rozhraní .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) na webu podpory společnosti Microsoft.

Toto téma obsahuje následující oddíly:

- [Proces nasazení](#the_deployment_process)
- [Nasazení rozhraní .NET Framework](#deploying_in_a_test_environment)
- [Vytvoření kolekce](#creating_a_collection)
- [Vytvoření balíčku a programu](#creating_a_package)
- [Výběr distribučního bodu](#select_dist_point)
- [Nasazení balíčku](#deploying_package)
- [Materiály](#resources)
- [Řešení potíží](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Proces nasazení

Pokud máte podpůrnou infrastrukturu na místě, použijte nástroj Configuration Manager k nasazení redistribuovatelného balíčku rozhraní .NET Framework do počítačů v síti. Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.

- Kolekce jsou **skupiny** prostředků nástroje Configuration Manager, například uživatelé, skupiny uživatelů nebo počítače, do kterých je nasadit rozhraní .NET Framework. Další informace naleznete [v tématu Úvod do kolekcí ve Správci konfigurace](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace nástroje Configuration Manager.

- **Balíčky a programy** obvykle představují softwarové aplikace, které mají být nainstalovány v klientském počítači, ale mohou také obsahovat jednotlivé soubory, aktualizace nebo dokonce jednotlivé příkazy. Další informace naleznete [v tématu Balíčky a programy ve Správci konfigurace](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) v knihovně dokumentace nástroje Configuration Manager.

- **Distribuční body** jsou role systému lokality nástroje Configuration Manager, které ukládají soubory potřebné ke spuštění softwaru v klientských počítačích. Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace. Další informace naleznete [v tématu Základní koncepty pro správu obsahu ve Správci konfigurace](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) v knihovně dokumentace nástroje Configuration Manager.

- **Nasazení instruují** příslušné členy zadané cílové kolekce k instalaci softwarového balíčku.

> [!IMPORTANT]
> Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení. Další možnosti nasazení nástroje Configuration Manager naleznete v [knihovně dokumentace nástroje Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>Nasazení rozhraní .NET Framework

Nástroj Configuration Manager můžete použít k nasazení tiché instalace rozhraní .NET Framework 4.5, kde uživatelé nepracují s procesem instalace. Postupujte následovně:

1. [Vytvořte kolekci](#creating_a_collection).

2. [Vytvořte balíček a program pro redistribuovatelné rozhraní .NET Framework](#creating_a_package).

3. [Vyberte distribuční bod](#select_dist_point).

4. [Nasazení balíčku](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Vytvoření kolekce

V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení. Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií). Další informace o pravidlech členství, včetně dotazů a přímých pravidel, naleznete [v tématu Úvod do kolekcí ve Správci konfigurace](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace nástroje Configuration Manager.

Postup vytvoření kolekce:

1. V konzole Nástroje pro přizpůsobení zvolte **Prostředky a dodržování předpisů**.

2. V pracovním prostoru **Prostředky a dodržování předpisů** zvolte Kolekce **zařízení**.

3. Na kartě **Domů** ve skupině **Vytvořit** zvolte **Vytvořit kolekci zařízení**.

4. Na stránce **Obecné** **průvodce vytvořením kolekce zařízení**zadejte název kolekce.

5. Zvolte **Procházet** a určete omezující kolekci.

6. Na stránce **Pravidla členství** zvolte **Přidat pravidlo**a pak zvolte Přímé **pravidlo,** chcete-li otevřít **Průvodce vytvořením pravidla přímého členství**. Zvolte **Další**.

7. Na stránce **Hledat zdroje** v seznamu **Třídy prostředků** zvolte Systémové **prostředky**. V seznamu **Název atributu** zvolte **Název**. Do pole **Hodnota** `%`zadejte a pak zvolte **Další**.

8. Na stránce **Vybrat prostředky** zaškrtněte políčko pro každý počítač, do kterého chcete nasadit rozhraní .NET Framework. Zvolte **Další**a dokončete průvodce.

9. Na stránce **Pravidla členství** průvodce **vytvořením kolekce zařízení**zvolte **Další**a dokončete průvodce.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework

Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework. Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.

Postup vytvoření balíčku:

1. V konzole Configuration Manager zvolte **Knihovna softwaru**.

2. V pracovním prostoru **Knihovna softwaru** rozbalte **položku Správa aplikací**a pak zvolte **Balíčky**.

3. Na kartě **Domů** ve skupině **Vytvořit** zvolte **Vytvořit balíček**.

4. Na stránce **Balíček** **Průvodce vytvořením balíčku a programu**zadejte následující informace:

    - Jméno:`.NET Framework 4.5`

    - Výrobce:`Microsoft`

    - Jazyk. `English (US)`

5. Zvolte **Tento balíček obsahuje zdrojové soubory**a pak zvolte **Procházet** a vyberte místní nebo síťovou složku, která obsahuje instalační soubory rozhraní .NET Framework. Po výběru složky zvolte **OK**a pak zvolte **Další**.

6. Na stránce **Typ programu** průvodce zvolte **Standardní program**a pak zvolte **Další**.

7. Na stránce **Program** **Průvodce vytvořením balíčku a programu**zadejte následující informace:

    1. **Název:**`.NET Framework 4.5`

    2. **Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (možnosti příkazového řádku jsou popsány v tabulce po těchto krocích)

    3. **Spustit:** Zvolte **Skryté**.

    4. **Program lze spustit:** Zvolte možnost, která určuje, že program lze spustit bez ohledu na to, zda je uživatel přihlášen.

8. Na stránce **Požadavky** zvolte **Další,** chcete-li přijmout výchozí hodnoty, a pak průvodce dokončete.

Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.

|Možnost|Popis|
|------------|-----------------|
|**/q**|Nastaví tichý režim. Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.|
|**/norestart**|Zabrání instalačnímu programu v automatickém restartování. Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.|
|**/chainingpackage** *PackageName*|Určuje název balíčku, který provádí řetězení. Tyto informace jsou uvedeny spolu s dalšími informacemi o relaci instalace pro ty, kteří se zaregistrovali do programu Zlepšování softwaru a služeb na základě zkušeností uživatelů společnosti Microsoft. Pokud název balíčku obsahuje mezery, použijte jako oddělovače dvojité uvozovky; například: **/chainingpackage "Chaining Product"**.|

Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5. Program provede nasazení tiché instalace rozhraní .NET Framework 4.5. V tiché instalaci uživatelé nepracují s procesem instalace a řetězení aplikace musí zachytit návratový kód a zpracování restartování; Viz [Získání informací o průběhu z instalačního balíčku](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Výběr distribučního bodu

Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.

Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:

1. V konzole Configuration Manager zvolte **Knihovna softwaru**.

2. V pracovním prostoru **Knihovna softwaru** rozbalte **položku Správa aplikací**a pak zvolte **Balíčky**.

3. Ze seznamu balíčků vyberte balíček **.NET Framework 4.5,** který jste vytvořili v předchozí části.

4. Na kartě **Domů** ve skupině **Nasazení** zvolte **Distribuovat obsah**.

5. Na kartě **Obecné** v **Průvodci distribucí obsahu**zvolte **Další**.

6. Na stránce **Cíl obsahu** průvodce zvolte **Přidat**a pak zvolte **Distribuční bod**.

7. V dialogovém okně **Přidat distribuční body** vyberte distribuční body, které budou hostitelem balíčku a programu, a pak zvolte **OK**.

8. Dokončete průvodce.

Balíček nyní obsahuje všechny informace, které potřebujete pro tiché nasazení rozhraní .NET Framework 4.5. Před nasazením balíčku a programu ověřte, zda byl nainstalován v distribučním bodě. V knihovně dokumentace nástroje Configuration Manager se v části Sledování stavu obsahu monitoru naleznete v části Sledování stavu [obsahu, který distribuujete pomocí nástroje Configuration Manager.](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed)

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Nasazení balíčku

Postup nasazení balíčku a programu .NET Framework 4.5:

1. V konzole Configuration Manager zvolte **Knihovna softwaru**.

2. V pracovním prostoru **Knihovna softwaru** rozbalte **položku Správa aplikací**a pak zvolte **Balíčky**.

3. Ze seznamu balíčků vyberte balíček, který jste vytvořili s názvem **.NET Framework 4.5**.

4. Na kartě **Domů** ve skupině **Nasazení** zvolte **Nasazení**.

5. Na stránce **Obecné** **průvodce nasazením softwaru**zvolte **Procházet**a vyberte kolekci, kterou jste vytvořili dříve. Zvolte **Další**.

6. Na stránce **Obsah** průvodce ověřte, zda se zobrazí bod, ze kterého chcete software distribuovat, a pak zvolte **Další**.

7. Na stránce **Nastavení nasazení** průvodce zkontrolujte, zda je **akce** nastavena na **nainstalovat**a **účel** je nastaven na **povinné**. Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích. Zvolte **Další**.

8. Na stránce **Plánování** průvodce určete, kdy má být rozhraní .NET Framework nainstalováno. Můžete zvolit **Nový** pro přiřazení času instalace nebo pokyn, aby software nainstaloval, když se uživatel přihlásí nebo vypne, nebo co nejdříve. Zvolte **Další**.

9. Na stránce **Uživatelské prostředí** průvodce použijte výchozí hodnoty a zvolte **Další**.

    > [!WARNING]
    > Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení. Informace o těchto možnostech naleznete v [tématu Vlastnosti názvu inzerce: Karta Plán](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Na stránce **Distribuční body** průvodce použijte výchozí hodnoty a zvolte **Další**.

11. Dokončete průvodce. Průběh nasazení můžete sledovat v uzlu **Nasazení** pracovního prostoru **monitorování.**

Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5. Informace o kódech chyb instalace rozhraní .NET Framework 4.5 naleznete v části [Návratové kódy](#return_codes) dále v tomto tématu.

<a name="resources"></a>

## <a name="resources"></a>Zdroje informací

Další informace o infrastruktuře pro testování nasazení balíčku .NET Framework 4.5 redistributable naleznete v následujících zdrojích.

**Active Directory, DNS, DHCP:**

- [Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [DNS (Domain Name System)](/windows-server/networking/dns/dns-top)

- [Protokol DHCP](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008:**

- [Instalace serveru SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [Přehled zabezpečení serveru SQL Server 2008 pro správce databáze](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**System Center 2012 Configuration Manager (Bod správy, distribuční bod):**

- [Správa lokality pro nástroj System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Konfigurační manažer plánování a nasazení jedné lokality](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Klient nástroje System Center 2012 Configuration Manager pro počítače se systémem Windows:**

- [Nasazení klientů pro nástroj System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Řešení potíží

### <a name="log-file-locations"></a>Umístění souborů protokolu

Následující soubory protokolu jsou generovány během instalace rozhraní .NET Framework:

- %temp%\Microsoft .NET Framework *verze*\*.txt
- %temp%\Microsoft .NET Framework *verze*\*.html

kde *verze* je verze rozhraní .NET Framework, kterou instalujete, například 4.5 nebo 4.7.2.

Můžete také určit adresář, do kterého jsou `/log` soubory protokolu zapsány, pomocí možnosti příkazového řádku v instalačním příkazu rozhraní .NET Framework. Další informace naleznete v [příručce k nasazení rozhraní .NET Framework pro vývojáře](deployment-guide-for-developers.md#command-line-options).

Pomocí nástroje [pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493) můžete shromažďovat soubory protokolu rozhraní .NET Framework a vytvořit soubor komprimované skříně (.cab), který zmenšuje velikost souborů.

<a name="return_codes"></a>

### <a name="return-codes"></a>Návratové kódy

V následující tabulce jsou uvedeny nejběžnější návratové kódy z redistribuovatelného instalačního programu rozhraní .NET Framework 4.5. Návratové kódy jsou stejné pro všechny verze instalačního programu.

Odkazy na podrobné informace naleznete v další části [Stažení kódů chyb](#additional_error_codes).

|Návratový kód|Popis|
|-----------------|-----------------|
|0|Instalace byla úspěšně dokončena.|
|1602|Instalace byla zrušena uživatelem.|
|1603|Při instalaci došlo k závažné chybě.|
|1641|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|3010|K dokončení instalace je nutné provést restart. Tato zpráva znamená úspěch.|
|5100|Počítač uživatele nesplňuje požadavky systému.|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a>Kódy chyb stahování

- [Kódy chyb služby INTELIGENTNÍ PŘENOS na pozadí (BITS)](/windows/desktop/Bits/bits-return-values)

- [Kódy chyb zástupný název adresy URL](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [Kódy chyb WinHttp](/windows/desktop/WinHttp/error-messages)

Další kódy chyb:

- [Kódy chyb Instalační služby systému Windows](/windows/desktop/msi/error-codes)

- [Kódy výsledků agenta služby Windows Update](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Viz také

- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Systémové požadavky](../get-started/system-requirements.md)
