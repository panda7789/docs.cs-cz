---
title: .NET Framework – průvodce nasazením pro administrátory
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91099b9b4d230839bc14c5fe4d5eafd05ac95541
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052148"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework – průvodce nasazením pro administrátory

V tomto podrobném článku se dozvíte, jak může správce systému nasadit .NET Framework 4,5 a jeho systémové závislosti v síti pomocí Microsoft System Center Configuration Manager. V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework. Seznam požadavků na software a hardware pro instalaci .NET Framework 4,5 najdete v tématu [požadavky na systém](../get-started/system-requirements.md).

> [!NOTE]
> Software odkazovaný v tomto dokumentu, včetně, bez omezení, .NET Framework 4,5, System Center Configuration Manager a Active Directory, podléhá licenčním podmínkám a podmínkám. V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je. Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.
>
> Informace o podpoře pro .NET Framework najdete v tématu [Zásady životního cyklu podpory Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) na webu Podpora Microsoftu.

Toto téma obsahuje následující oddíly:

- [Proces nasazení](#the_deployment_process)
- [Nasazení rozhraní .NET Framework](#deploying_in_a_test_environment)
- [Vytvoření kolekce](#creating_a_collection)
- [Vytvoření balíčku a programu](#creating_a_package)
- [Vyberte distribuční bod](#select_dist_point)
- [Nasadit balíček](#deploying_package)
- [Prostředky](#resources)
- [Odstraňování potíží](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Proces nasazení

Pokud je k dispozici podpůrná infrastruktura, lze distribuovatelný balíček rozhraní .NET Framework nasadit na počítače v síti pomocí nástroje System Center 2012 Configuration Manager. Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.

- **Kolekce** jsou skupiny Configuration Manager prostředků, jako jsou uživatelé, skupiny uživatelů nebo počítače, do kterých se .NET Framework nasadí. Další informace najdete v tématu [Úvod do kolekcí v System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace Configuration Manager.

- **Balíčky a programy** obvykle představují softwarové aplikace, které mají být nainstalovány v klientském počítači, ale mohou obsahovat také jednotlivé soubory, aktualizace nebo dokonce jednotlivé příkazy. Další informace najdete v tématu [balíčky a programy v System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) v knihovně dokumentace Configuration Manager.

- **Distribuční body** jsou Configuration Manager role systému lokality, které ukládají soubory požadované pro spuštění softwaru na klientských počítačích. Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace. Další informace najdete v tématu [základní koncepty správy obsahu v Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) v knihovně dokumentace Configuration Manager.

- **Nasazení** instruují příslušné členy zadané cílové kolekce k instalaci softwarového balíčku.

> [!IMPORTANT]
> Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení. Další možnosti nasazení Configuration Manager najdete v [knihovně dokumentace Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>Nasazení rozhraní .NET Framework

Pomocí nástroje System Center 2012 Configuration Manager můžete nasadit tichou instalaci .NET Framework 4,5, kde uživatelé nepracují s procesem instalace. Postupujte podle těchto kroků:

1. [Vytvořte kolekci](#creating_a_collection).

2. [Vytvořte balíček a program pro .NET Framework redistributable](#creating_a_package).

3. [Vyberte distribuční bod](#select_dist_point).

4. [Nasaďte balíček](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Vytvoření kolekce

V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení. Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií). Další informace o pravidlech členství, včetně dotazů a přímých pravidel, najdete v tématu [Úvod do kolekcí v System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace Configuration Manager.

Postup vytvoření kolekce:

1. V konzole Configuration Manager vyberte **prostředky a kompatibilita**.

2. V pracovním prostoru **prostředky a kompatibilita** vyberte **kolekce zařízení**.

3. Na kartě **Domů** ve skupině **vytvořit** vyberte možnost **vytvořit kolekci zařízení**.

4. Na stránce **Obecné** v **Průvodci vytvořením kolekce zařízení**zadejte název kolekce.

5. Zvolte **Procházet** a zadejte omezující kolekci.

6. Na stránce **pravidla členství** zvolte možnost **Přidat pravidlo**a pak zvolte možnost **přímé pravidlo** . otevře se **Průvodce vytvořením pravidla přímého členství**. Zvolte **Další**.

7. Na stránce **Hledat prostředky** v seznamu **Třída prostředků** vyberte položku **systémový prostředek**. V seznamu **název atributu** vyberte možnost **název**. Do pole **hodnota** zadejte `%`a klikněte na tlačítko **Další**.

8. Na stránce **vybrat prostředky** zaškrtněte políčko u každého počítače, do kterého chcete nasadit .NET Framework. Klikněte na tlačítko **Další**a dokončete průvodce.

9. Na stránce **pravidla členství** v **Průvodci vytvořením kolekce zařízení**klikněte na tlačítko **Další**a dokončete průvodce.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework

Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework. Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.

Postup vytvoření balíčku:

1. V konzole Configuration Manager vyberte možnost **softwarová knihovna**.

2. V pracovním prostoru **softwarová knihovna** rozbalte položku **Správa aplikací**a pak zvolte možnost **balíčky**.

3. Na kartě **Domů** ve skupině **vytvořit** klikněte na možnost **vytvořit balíček**.

4. Na stránce **balíček** v **Průvodci vytvořením balíčku a programu**zadejte následující informace:

    - Jméno:`.NET Framework 4.5`

    - Výrobců`Microsoft`

    - Jazyk. `English (US)`

5. Zvolte **Tento balíček obsahuje zdrojové soubory**a pak zvolte **Procházet** a vyberte místní nebo síťovou složku, která obsahuje instalační soubory .NET Framework. Po výběru složky klikněte na **tlačítko OK**a potom na tlačítko **Další**.

6. Na stránce **typ programu** v průvodci zvolte možnost **standardní program**a klikněte na tlačítko **Další**.

7. Na stránce **program** v **Průvodci vytvořením balíčku a programu**zadejte následující informace:

    1. **Název:** `.NET Framework 4.5`

    2. **Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (možnosti příkazového řádku jsou popsané v tabulce po těchto krocích)

    3. **Spouštěl** Vyberte **skrytý**.

    4. **Program lze spustit:** Vyberte možnost, která určuje, zda může program běžet bez ohledu na to, zda je uživatel přihlášen.

8. Na stránce **požadavky** kliknutím na tlačítko **Další** přijměte výchozí hodnoty a pak dokončete průvodce.

Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.

|Možnost|Popis|
|------------|-----------------|
|**/q**|Nastaví tichý režim. Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.|
|**/ norestart /**|Zabrání instalačnímu programu v automatickém restartování. Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.|
|**/chainingpackage** Soubor s *balíčkem*|Určuje název balíčku, který provádí řetězení. Tyto informace jsou hlášeny s dalšími informacemi o Instalační relaci pro ty, kteří se zaregistrovali v [programu Microsoft program Zlepšování softwaru a služeb na základě zkušeností uživatelů (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244). Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače. Příklad: **/chainingpackage "řetězení produktu"** .|

Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5. Program provede nasazení tiché instalace rozhraní .NET Framework 4.5. V tiché instalaci uživatelé nepracují s procesem instalace a zřetězená aplikace musí zachytit návratový kód a zpracovat restartování. viz [získání informací o průběhu z instalačního balíčku](https://go.microsoft.com/fwlink/?LinkId=179606).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Výběr distribučního bodu

Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.

Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:

1. V konzole Configuration Manager vyberte možnost **softwarová knihovna**.

2. V pracovním prostoru **softwarová knihovna** rozbalte položku **Správa aplikací**a pak zvolte možnost **balíčky**.

3. V seznamu balíčků vyberte balíček **.NET Framework 4,5** , který jste vytvořili v předchozí části.

4. Na kartě **Domů** ve skupině **nasazení** klikněte na možnost **distribuovat obsah**.

5. Na kartě **Obecné** v **Průvodci distribucí obsahu**klikněte na tlačítko **Další**.

6. Na stránce **cíl obsahu** průvodce zvolte možnost **Přidat**a pak zvolte možnost **distribuční bod**.

7. V dialogovém okně **Přidat distribuční body** vyberte distribuční body, které budou hostovat balíček a program a klikněte na **tlačítko OK**.

8. Dokončete průvodce.

Balíček nyní obsahuje všechny informace, které potřebujete pro tiché nasazení rozhraní .NET Framework 4.5. Před nasazením balíčku a programu ověřte, zda byl nainstalován v distribučním bodě. v části monitorování obsahu v tématu [sledování obsahu distribuovaného pomocí System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) v knihovně dokumentace Configuration Manager.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Nasazení balíčku

Postup nasazení balíčku a programu .NET Framework 4.5:

1. V konzole Configuration Manager vyberte možnost **softwarová knihovna**.

2. V pracovním prostoru **softwarová knihovna** rozbalte položku **Správa aplikací**a pak zvolte možnost **balíčky**.

3. V seznamu balíčků vyberte balíček, který jste vytvořili s názvem **.NET Framework 4,5**.

4. Na kartě **Domů** ve skupině **nasazení** klikněte na možnost **nasadit**.

5. Na stránce **Obecné** v **Průvodci nasazením softwaru**klikněte na tlačítko **Procházet**a poté vyberte kolekci, kterou jste vytvořili dříve. Zvolte **Další**.

6. Na stránce **obsah** v průvodci ověřte, zda je zobrazen bod, ze kterého chcete distribuovat software, a pak zvolte možnost **Další**.

7. Na stránce **nastavení nasazení** v průvodci potvrďte, že **Akce** je nastavená na **instalovat**a **účel** je nastavený na **požadováno**. Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích. Zvolte **Další**.

8. Na stránce **plánování** v průvodci určete, kdy chcete .NET Framework nainstalovat. Můžete zvolit možnost **nové** a přiřadit čas instalace nebo dát pokyn k instalaci softwaru, když se uživatel přihlásí nebo vypíná nebo co nejdříve. Zvolte **Další**.

9. Na stránce **činnost koncového uživatele** v průvodci použijte výchozí hodnoty a klikněte na tlačítko **Další**.

    > [!WARNING]
    > Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení. Informace o těchto možnostech najdete v tématu [vlastnosti názvu inzerce: Karta](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29)plán

10. Na stránce **distribuční body** v průvodci použijte výchozí hodnoty a klikněte na tlačítko **Další**.

11. Dokončete průvodce. Průběh nasazení můžete sledovat v uzlu **nasazení** v pracovním prostoru **monitorování** .

Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5. Informace o kódech chyb instalace .NET Framework 4,5 naleznete v části [návratové kódy](#return_codes) dále v tomto tématu.

<a name="resources"></a>

## <a name="resources"></a>Prostředky

Další informace o infrastruktuře pro testování nasazení .NET Framework 4,5 Distribuovatelný balíček najdete v následujících zdrojích informací.

**Active Directory, DNS, DHCP:**

- [Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [DNS (Domain Name System)](/windows-server/networking/dns/dns-top)

- [Protokol DHCP (Dynamic Host Configuration Protocol)](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008:**

- [Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [Přehled zabezpečení SQL Server 2008 pro správce databáze](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**System Center 2012 Configuration Manager (bod správy, distribuční bod):**

- [Správa lokality pro System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Configuration Manager plánování a nasazení v jednom webu](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Klient System Center 2012 Configuration Manager klienta pro počítače se systémem Windows:**

- [Nasazení klientů pro System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Poradce při potížích

### <a name="log-file-locations"></a>Umístění souborů protokolu

Během .NET Frameworkho nastavení se generují následující soubory protokolu:

- %Temp%\Microsoft .NET Framework *verze*\*. txt
- %Temp%\Microsoft .NET Framework *verze*\*. html

kde *verze* je verze .NET Framework, kterou instalujete, například 4,5 nebo 4.7.2.

Můžete taky určit adresář, do kterého se budou zapisovat soubory protokolu, a to `/log` pomocí možnosti příkazového řádku v instalačním příkazu .NET Framework. Další informace najdete v tématu [Průvodce nasazením .NET Framework pro vývojáře](deployment-guide-for-developers.md#command-line-options).

[Nástroj pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493) můžete použít ke shromáždění souborů protokolu .NET Framework a k vytvoření komprimovaného souboru CAB (. cab), který zmenší velikost souborů.

<a name="return_codes"></a>

### <a name="return-codes"></a>Návratové kódy

Následující tabulka uvádí nejběžnější návratové kódy z instalačního programu .NET Framework 4,5 Redistributable. Návratové kódy jsou stejné pro všechny verze instalačního programu.

Odkazy na podrobné informace naleznete v další části, [stažení kódů chyb](#additional_error_codes).

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

- [Kódy chyb Background Intelligent Transfer Service (BITS)](/windows/desktop/Bits/bits-return-values)

- [Kódy chyb monikeru URL](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [Kódy chyb služby WinHttp](/windows/desktop/WinHttp/error-messages)

Další kódy chyb:

- [Kódy chyb Instalační služba systému Windows](/windows/desktop/msi/error-codes)

- [web Windows Update kódy výsledků agenta](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Viz také:

- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Požadavky na systém](../get-started/system-requirements.md)
