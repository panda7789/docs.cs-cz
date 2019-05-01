---
title: .NET Framework – průvodce nasazením pro administrátory
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7157c1fc6084713a4a565d21beb20563b2135cd9
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807915"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework – průvodce nasazením pro administrátory

Tento článek popisuje, jak může správce systému nasadit [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho systémové závislosti napříč sítí pomocí nástroje System Center Configuration Manager. V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework. Seznam všech softwarových a hardwarových požadavků pro instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], naleznete v tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).

> [!NOTE]
> Software zmíněný v tomto dokumentu, včetně mimo jiné [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager a služby Active Directory, se vztahují licenční podmínky a ujednání. V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je. Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.
>
> Informace o podpoře pro rozhraní .NET Framework najdete v tématu [podporu zásad životního cyklu Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) na webu Microsoft Support.

Toto téma obsahuje následující oddíly:

- [Proces nasazení](#the_deployment_process)
- [Nasazení rozhraní .NET Framework](#deploying_in_a_test_environment)
- [Vytvoření kolekce](#creating_a_collection)
- [Vytvoření balíčku a programu](#creating_a_package)
- [Vyberte distribuční bod](#select_dist_point)
- [Nasazení balíčku](#deploying_package)
- [Prostředky](#resources)
- [Odstraňování potíží](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Proces nasazení

Pokud je k dispozici podpůrná infrastruktura, lze distribuovatelný balíček rozhraní .NET Framework nasadit na počítače v síti pomocí nástroje System Center 2012 Configuration Manager. Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.

- **Kolekce** jsou skupiny prostředků nástroje Configuration Manager, jako jsou uživatelé, skupiny uživatelů nebo počítačů, u kterých je nasazení rozhraní .NET Framework. Další informace najdete v tématu [seznámení s kolekcemi v nástroji System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace nástroje Configuration Manager.

- **Balíčky a programy** představují většinou softwarové aplikace nainstalovat na klientský počítač, ale mohou také obsahovat jednotlivé soubory, aktualizace nebo dokonce jednotlivé příkazy. Další informace najdete v tématu [balíčků a programů v nástroji System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) v knihovně dokumentace nástroje Configuration Manager.

- **Distribuční body** lokalitu nástroje Configuration Manager jsou role systému, které ukládají soubory nezbytné pro ke spuštění softwaru na klientských počítačích. Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace. Další informace najdete v tématu [základní koncepty správy obsahu v nástroji Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) v knihovně dokumentace nástroje Configuration Manager.

- **Nasazení** pověří příslušné členy zadané cílové kolekce k instalaci softwarového balíčku.

> [!IMPORTANT]
> Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení. Další možnosti nasazení nástroje Configuration Manager, najdete v článku [knihovně dokumentace nástroje Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>Nasazení rozhraní .NET Framework

System Center 2012 Configuration Manager můžete použít k nasazení tiché instalace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kde uživatelé nespolupracují s instalačním procesem. Postupujte podle těchto kroků:

1. [Vytvoření kolekce](#creating_a_collection).

2. [Vytvoření balíčku a programu pro rozhraní .NET Framework redistributable](#creating_a_package).

3. [Vyberte distribuční bod](#select_dist_point).

4. [Nasazení balíčku](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Vytvoření kolekce

V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení. Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií). Další informace o pravidlech členství, včetně dotazů a přímých pravidel, naleznete v tématu [seznámení s kolekcemi v nástroji System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace nástroje Configuration Manager.

Postup vytvoření kolekce:

1. V konzole nástroje Configuration Manager, zvolte **prostředky a Kompatibilita**.

2. V **prostředky a Kompatibilita** pracovního prostoru, zvolte **kolekce zařízení**.

3. Na **Domů** kartu **vytvořit** skupině, zvolte **vytvořit kolekci zařízení**.

4. Na **Obecné** stránku **Průvodce vytvořením kolekce zařízení**, zadejte název kolekce.

5. Zvolte **Procházet** určit limitující kolekci.

6. Na **pravidla členství** zvolte **přidat pravidlo**a klikněte na tlačítko **přímého pravidla** otevřít **vytvořením pravidla přímého členství**. Zvolte **Další**.

7. Na **hledat prostředky** stránku, **třídy prostředků** klikněte na položku **systémový prostředek**. V **název atributu** klikněte na položku **název**. V **hodnotu** zadejte `%`a klikněte na tlačítko **Další**.

8. Na **vyberte prostředky** stránce, zaškrtněte políčko pro každý počítač, který chcete nasadit rozhraní .NET Framework. Zvolte **Další**a poté průvodce dokončete.

9. Na **pravidla členství** stránku **Průvodce vytvořením kolekce zařízení**, zvolte **Další**a poté průvodce dokončete.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework

Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework. Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.

Postup vytvoření balíčku:

1. V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.

2. V **softwarová knihovna** pracovního prostoru, rozbalte **správy aplikací**a klikněte na tlačítko **balíčky**.

3. Na **Domů** kartě **vytvořit** skupině, zvolte **vytvořit balíček**.

4. Na **balíčku** stránku **Průvodce vytvoření balíčku a programu**, zadejte následující informace:

    - Jméno: `.NET Framework 4.5`

    - Výrobce: `Microsoft`

    - Jazyk. `English (US)`

5. Zvolte **tento balíček obsahuje zdrojové soubory**a klikněte na tlačítko **Procházet** vyberte místní nebo síťovou složku, která obsahuje instalační soubory rozhraní .NET Framework. Když vyberete složku, zvolte **OK**a klikněte na tlačítko **Další**.

6. Na **typ programu** stránku průvodce, zvolte **standardní Program**a klikněte na tlačítko **Další**.

7. Na **Program** stránku **Průvodce vytvoření balíčku a programu**, zadejte následující informace:

    1. **Jméno:** `.NET Framework 4.5`

    2. **Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Možnosti příkazového řádku jsou popsané v tabulce po provedení těchto kroků)

    3. **Spusťte:** Zvolte **skryté**.

    4. **Program lze spustit:** Zvolte si možnost, která určuje, že program může spustit, bez ohledu na to, zda je přihlášený uživatel.

8. Na **požadavky** zvolte **Další** přijmout výchozí hodnoty a pak dokončete průvodce.

Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.

|Možnost|Popis|
|------------|-----------------|
|**/q**|Nastaví tichý režim. Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.|
|**/ norestart /**|Zabrání instalačnímu programu v automatickém restartování. Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.|
|**chainingpackage** *název balíčku*|Určuje název balíčku, který provádí řetězení. Tato informace je oznámena spolu s dalšími informacemi relace instalace pro ty, kteří se přihlásili k odběru [Microsoft zkušeností zlepšování Program uživatelů (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244). Pokud název balíčku obsahuje mezery, použijte uvozovky jako oddělovače; Příklad: **chainingpackage "Chaining Product"**.|

Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5. Program provede nasazení tiché instalace rozhraní .NET Framework 4.5. V případě tiché instalace uživatelé nespolupracují s instalačním procesem a zřetězující aplikace musí zachytit návratový kód a zpracovat restartování; Zobrazit [získávání informací o průběhu z instalačního balíčku](https://go.microsoft.com/fwlink/?LinkId=179606).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Výběr distribučního bodu

Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.

Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:

1. V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.

2. V **softwarová knihovna** pracovního prostoru, rozbalte **správy aplikací**a klikněte na tlačítko **balíčky**.

3. Ze seznamu balíčků vyberte balíček **rozhraní .NET Framework 4.5** , kterou jste vytvořili v předchozí části.

4. Na **Domů** kartě **nasazení** skupině, zvolte **distribuovat obsah**.

5. Na **Obecné** karty **Průvodce distribucí obsahu**, zvolte **Další**.

6. Na **cílové umístění obsahu** stránku průvodce, zvolte **přidat**a klikněte na tlačítko **distribuční bod**.

7. V **přidat distribuční body** dialogového okna, vyberte distribuční body, který bude hostovat balíček a program a klikněte na tlačítko **OK**.

8. Dokončete průvodce.

Balíček nyní obsahuje všechny informace, které potřebujete pro tiché nasazení rozhraní .NET Framework 4.5. Před nasazením balíčku a programu ověřte, zda byl nainstalován v distribučním bodě; najdete v části "Monitorování obsahu" [monitorovat obsah, který jste distribuovali pomocí nástroje System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) v knihovně dokumentace nástroje Configuration Manager.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Nasazení balíčku

Postup nasazení balíčku a programu .NET Framework 4.5:

1. V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.

2. V **softwarová knihovna** pracovního prostoru, rozbalte **správy aplikací**a klikněte na tlačítko **balíčky**.

3. Ze seznamu balíčků vyberte balíček, je vytvořena s názvem **rozhraní .NET Framework 4.5**.

4. Na **Domů** kartě **nasazení** skupině, zvolte **nasadit**.

5. Na **Obecné** stránku **Průvodce nasazením softwaru**, zvolte **Procházet**a pak vyberte aplikaci, kterou jste vytvořili dříve. Zvolte **Další**.

6. Na **obsahu** stránku průvodce, ověřte, zda se zobrazí bodu, ze kterého chcete software distribuovat a klikněte na tlačítko **Další**.

7. Na **nastavení nasazení** stránku průvodce, ujistěte se, že **akce** je nastavena na **nainstalovat**, a **účel** je nastavena na **Vyžaduje**. Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích. Zvolte **Další**.

8. Na **plánování** stránku průvodce, určete, kdy má být nainstalované rozhraní .NET Framework. Můžete zvolit **nový** přiřadit čas instalace nebo dáte pokyn, aby software pro instalaci, když se uživatel přihlásí na nebo vypnutá nebo co nejdříve. Zvolte **Další**.

9. Na **činnost koncového uživatele** stránku průvodce, použijte výchozí hodnoty a vyberte možnost **Další**.

    > [!WARNING]
    > Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení. Informace o těchto možnostech najdete v tématu [vlastnosti názvu ohlášení: Naplánovat kartu](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Na **distribučních bodů** stránku průvodce, použijte výchozí hodnoty a vyberte možnost **Další**.

11. Dokončete průvodce. Průběh nasazení můžete monitorovat **nasazení** uzlu **monitorování** pracovního prostoru.

Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5. Informace o chybových kódech instalace rozhraní .NET Framework 4.5, najdete v článku [návratové kódy](#return_codes) později v tomto tématu.

<a name="resources"></a>

## <a name="resources"></a>Prostředky

Další informace o infrastruktuře pro testovaní nasazení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Distribuovatelný balíček, najdete v následujících zdrojích informací.

**Active Directory, DNS, DHCP:**

- [Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [Domain Name System (DNS)](/windows-server/networking/dns/dns-top)

- [Dynamic Host Configuration Protocol (DHCP)](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008:**

- [Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [Přehled zabezpečení služby SQL Server 2008 pro správce databáze](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**System Center 2012 Configuration Manager (bod správy, distribuční bod):**

- [Správa lokality pro System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Na jednom webu nástroje Configuration Manager plánování a nasazení](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Klient System Center 2012 Configuration Manager pro počítače s Windows:**

- [Nasazení klientů pro System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Poradce při potížích

### <a name="log-file-locations"></a>Umístění souborů protokolu

Následující soubory protokolu jsou generovány během instalace rozhraní .NET Framework:

- %temp%\Microsoft rozhraní .NET framework *verze*\*txt
- %temp%\Microsoft .NET Framework *version*\*.html

kde *verze* je verze rozhraní .NET Framework, které chcete instalovat, jako je například 4.5 nebo 4.7.2.

Můžete také zadat adresář, do protokolu, které soubory jsou zapsány pomocí `/log` možnost příkazového řádku v příkazu instalace rozhraní .NET Framework. Další informace najdete v tématu [rozhraní .NET Framework – Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md#command-line-options).

Můžete použít [nástroj pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493) shromažďovat soubory protokolů rozhraní .NET Framework a vytvořte komprimovaný soubor CAB (.cab) soubor, který redukuje velikost souborů.

<a name="return_codes"></a>

### <a name="return-codes"></a>Návratové kódy

Následující tabulka obsahuje nejběžnější návratové kódy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalačního programu opětovné distribuce. Návratové kódy jsou stejné pro všechny verze instalačního programu.

Odkazy na podrobné informace najdete v další části [kódy chyb stahování](#additional_error_codes).

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

- [Kódy chyb služby Background Intelligent Transfer Service (BITS)](/windows/desktop/Bits/bits-return-values)

- [Kódy chyb monikeru URL:](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [Kódy chyb služby WinHttp](/windows/desktop/WinHttp/error-messages)

Další kódy chyb:

- [Kódy chyb Instalační služby systému Windows](/windows/desktop/msi/error-codes)

- [Výsledné kódy agenta služby Windows Update](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Viz také:

- [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)
