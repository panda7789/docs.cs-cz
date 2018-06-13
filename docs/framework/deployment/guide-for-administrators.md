---
title: .NET Framework – průvodce nasazením pro administrátory
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b4c2d4205e87d8be21f82eaf74b17e316d9057e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394329"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework – průvodce nasazením pro administrátory
Tento článek podrobně popisuje, jak můžete nasadit správce systému [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho závislé součásti systému přes síť pomocí Microsoft System Center Configuration Manager. V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework. Seznam softwarové a hardwarové požadavky pro instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], najdete v části [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  Software v tomto dokumentu, včetně, ale bez omezení, odkazuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager a služby Active Directory, jsou všechny vztahují licenční podmínky a ujednání. V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je. Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.  
>   
>  Informace o podpoře pro rozhraní .NET Framework najdete v tématu [podporu zásadách životního cyklu Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) na webu Microsoft Support.  
  
 Toto téma obsahuje následující oddíly:  
  
 [Proces nasazení](#the_deployment_process)  
 [Nasazení rozhraní .NET Framework](#deploying_in_a_test_environment)  
 [Vytvoření kolekce](#creating_a_collection)  
 [Vytvoření balíčku a programu](#creating_a_package)  
 [Vyberte distribuční bod](#select_dist_point)  
 [Nasazení balíčku](#deploying_package)  
[Prostředky](#resources)  
[Odstraňování potíží](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>Proces nasazení  
 Pokud je k dispozici podpůrná infrastruktura, lze distribuovatelný balíček rozhraní .NET Framework nasadit na počítače v síti pomocí nástroje System Center 2012 Configuration Manager. Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.  
  
-   **Kolekce** jsou skupiny prostředků nástroje Configuration Manager, jako jsou uživatelé, skupiny uživatelů nebo počítačů, na kterých je nasazená rozhraní .NET Framework. Další informace najdete v tématu [kolekce v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) v knihovně dokumentace nástroje Configuration Manager.  
  
-   **Balíčky a programy** obvykle představují softwarové aplikace k instalaci na klientském počítači, ale může také obsahovat jednotlivé soubory, aktualizace nebo i jednotlivé příkazy. Další informace najdete v tématu [balíčků a programů v nástroji Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) v knihovně dokumentace nástroje Configuration Manager.  
  
-   **Distribuční body** lokality nástroje Configuration Manager jsou role systému, které obsahují soubory potřebné pro ke spuštění softwaru na klientských počítačích. Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace. Další informace najdete v tématu [Úvod do správy obsahu v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) v knihovně dokumentace nástroje Configuration Manager.  
  
-   **Nasazení** požádejte použít členy zadané cílové kolekce k instalaci balíčku softwaru. Další informace najdete v tématu [nasazení aplikací v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) v knihovně dokumentace nástroje Configuration Manager.  
  
> [!IMPORTANT]
>  Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení. Další možnosti nasazení nástroje Configuration Manager najdete v tématu [knihovně dokumentace nástroje Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>Nasazení rozhraní .NET Framework  
 Můžete nasadit tichou instalaci produktu System Center 2012 Configuration Manager [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kde uživatelé nespolupracuje s proces instalace. Postupujte podle těchto kroků:  
  
1.  [Vytvořte kolekci](#creating_a_collection).  
  
2.  [Vytvoření balíčku a programu pro rozhraní .NET Framework redistributable](#creating_a_package).  
  
3.  [Vyberte distribuční bod](#select_dist_point).  
  
4.  [Nasazení balíčku](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>Vytvoření kolekce  
 V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení. Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií). Další informace o pravidla členství, včetně dotazů a přímá pravidla, najdete v části [seznámení s kolekcemi v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) v knihovně dokumentace nástroje Configuration Manager.  
  
 Postup vytvoření kolekce:  
  
1.  V konzole nástroje Configuration Manager, zvolte **prostředky a Kompatibilita**.  
  
2.  V **prostředky a Kompatibilita** prostoru vyberte **kolekce zařízení**.  
  
3.  Na **Domů** ve **vytvořit** skupiny, vyberte **vytvořit kolekci zařízení**.  
  
4.  Na **Obecné** stránky **Průvodce vytvořením kolekce zařízení**, zadejte název kolekce.  
  
5.  Zvolte **Procházet** určit limitující kolekci.  
  
6.  Na **pravidla členství** vyberte **přidat pravidlo**a potom zvolte **přímého pravidla** otevřete **přímé členství v Průvodci vytvořením pravidla**. Zvolte **Další**.  
  
7.  Na **hledat prostředky** stránky v **Třída prostředků** vyberte **systémový prostředek**. V **název atributu** vyberte **název**. V **hodnotu** zadejte `%`a potom zvolte **Další**.  
  
8.  Na **vyberte prostředky** stránky, zaškrtněte políčko pro každý počítač, který chcete nasadit rozhraní .NET Framework. Zvolte **Další**a pak dokončete průvodce.  
  
9. Na **pravidla členství** stránky **Průvodce vytvořením kolekce zařízení**, zvolte **Další**a pak dokončete průvodce.  
  
 Další informace o kolekcích najdete v tématu [kolekce v nástroji Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) v knihovně dokumentace nástroje Configuration Manager.  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework  
 Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework. Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.  
  
 Postup vytvoření balíčku:  
  
1.  V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**...  
  
2.  V **softwarová knihovna** pracovního prostoru, rozbalte položku **Správa aplikací**a potom zvolte **balíčky**.  
  
3.  Na **Domů** ve **vytvořit** skupiny, vyberte **vytvořit balíček**.  
  
4.  Na **balíček** stránky **Průvodce vytvoření balíčku a programu**, zadejte následující informace:  
  
    -   Jméno: `.NET Framework 4.5`  
  
    -   Výrobce: `Microsoft`  
  
    -   Jazyk. `English (US)`  
  
5.  Zvolte **tento balíček obsahuje zdrojové soubory**a potom zvolte **Procházet** vybrat místní nebo síťové složky, která obsahuje instalační soubory rozhraní .NET Framework. Pokud jste vybrali složce, vyberte **OK**a potom zvolte **Další**.  
  
6.  Na **typ programu** stránky v průvodci vyberte **standardní Program**a potom vyberte **Další**.  
  
7.  Na **programu** stránky **Průvodce vytvoření balíčku a programu**, zadejte následující informace:  
  
    1.  **Jméno:** `.NET Framework 4.5`  
  
    2.  **Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Možnosti příkazového řádku jsou popsané v tabulce po provedení těchto kroků)  
  
    3.  **Spustit:** zvolte **skryté**.  
  
    4.  **Program lze spustit:** zvolte možnost, která určuje, zda může program spustit, bez ohledu na to, zda je přihlášený uživatel.  
  
8.  Na **požadavky** vyberte **Další** přijmout výchozí hodnoty a pak dokončete průvodce.  
  
 Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/q**|Nastaví tichý režim. Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.|  
|**/ norestart**|Zabrání instalačnímu programu v automatickém restartování. Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.|  
|**/chainingpackage** *název balíčku*|Určuje název balíčku, který provádí řetězení. Tyto informace, se použije v hlášení Další informace o instalaci relace pro ty, kteří si zaregistrovali [Microsoft zkušeností zlepšování Program uživatelů (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244). Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače; Příklad: **/chainingpackage "Řetězení produkt"**.|  
  
 Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5. Program provede nasazení tiché instalace rozhraní .NET Framework 4.5. Při tiché instalaci uživatelé nespolupracuje s proces instalace a k získání návratového kódu a zpracovat restartování; má řetězení aplikace v tématu [získávání informace o průběhu z instalačního balíku](http://go.microsoft.com/fwlink/?LinkId=179606).  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>Výběr distribučního bodu  
 Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.  
  
 Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:  
  
1.  V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.  
  
2.  V **softwarová knihovna** pracovního prostoru, rozbalte položku **Správa aplikací**a potom zvolte **balíčky**.  
  
3.  Seznam balíčků, vyberte balíček **rozhraní .NET Framework 4.5** kterou jste vytvořili v předchozí části.  
  
4.  Na **Domů** ve **nasazení** skupiny, vyberte **distribuovat obsah**.  
  
5.  Na **Obecné** kartě **Průvodce distribucí obsahu**, zvolte **Další**.  
  
6.  Na **cílové umístění obsahu** stránku průvodce, zvolte **přidat**a potom zvolte **distribuční bod**.  
  
7.  V **přidat distribuční body** dialogovém okně vyberte distribuční body, který bude hostitelem balíčku a programu a potom zvolte **OK**.  
  
8.  Dokončete průvodce.  
  
 Balíček nyní obsahuje všechny informace, které potřebujete pro tiché nasazení rozhraní .NET Framework 4.5. Před nasazením balíčku a programu, ověřte, zda byl nainstalován v distribučním bodě; najdete v části "Monitorování obsah" [operace a údržba pro správu obsahu v nástroji Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) v knihovně dokumentace nástroje Configuration Manager.  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>Nasazení balíčku  
 Postup nasazení balíčku a programu .NET Framework 4.5:  
  
1.  V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.  
  
2.  V **softwarová knihovna** pracovního prostoru, rozbalte položku **Správa aplikací**a potom zvolte **balíčky**.  
  
3.  Seznam balíčků, vyberte balíček, který jste vytvořili pojmenované **rozhraní .NET Framework 4.5**.  
  
4.  Na **Domů** ve **nasazení** skupiny, vyberte **nasadit**.  
  
5.  Na **Obecné** stránky **Průvodce nasazením softwaru**, zvolte **Procházet**a potom vyberte kolekci, kterou jste vytvořili dříve. Zvolte **Další**.  
  
6.  Na **obsahu** stránku průvodce, ověřte, zda se zobrazí bod, ze kterého chcete distribuovat software a potom zvolte **Další**.  
  
7.  Na **nastavení nasazení** stránku průvodce, potvrďte, že **akce** je nastaven na **nainstalovat**, a **účel** je nastaven na **Požadované**. Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích. Zvolte **Další**.  
  
8.  Na **plánování** stránku průvodce, určete, kdy má být nainstalované rozhraní .NET Framework. Můžete zvolit **nový** pro přiřazení času instalace, nebo instruovat software, který chcete nainstalovat, když se uživatel přihlásí na nebo vypnutí nebo co nejdříve. Zvolte **Další**.  
  
9. Na **činnost koncového uživatele** stránce průvodce, použijte výchozí hodnoty a zvolte **Další**.  
  
    > [!WARNING]
    >  Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení. Informace o těchto možnostech najdete v tématu [oznámení o inzerovaném programu název vlastnosti: kartu plán](http://technet.microsoft.com/library/bb694016.aspx) v knihovně TechNet.  
  
10. Na **distribuční body** stránce průvodce, použijte výchozí hodnoty a zvolte **Další**.  
  
11. Dokončete průvodce. Můžete sledovat průběh nasazení v **nasazení** uzlu **monitorování** pracovního prostoru.  
  
 Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5. Informace o kódy chyb instalace rozhraní .NET Framework 4.5, najdete v článku [návratové kódy](#return_codes) později v tomto tématu.  
  
<a name="resources"></a>   
## <a name="resources"></a>Prostředky  
 Další informace o infrastrukturu pro testování nasazení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Distribuovatelný balíček, najdete v následujících materiálech.  
  
 **Active Directory, DNS, DHCP:**  
  
-   [Active Directory Domain Services pro systém Windows Server 2008](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [DNS Server](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [DHCP Server](http://technet.microsoft.com/library/cc896553.aspx)  
  
 **SQL Server 2008:**  
  
-   [Instalace systému SQL Server 2008 (Video serveru SQL Server)](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [Přehled zabezpečení SQL Server 2008 pro správce databáze](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager (bod správy, distribuční bod):**  
  
-   [Správa lokality pro nástroj System Center 2012 Configuration Manager](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [Lokality nástroje Configuration Manager jedním plánování a nasazení](http://technet.microsoft.com/library/bb680961.aspx)  
  
 **System Center 2012 Configuration Manager klienta pro počítače se systémem Windows:**  
  
-   [Nasazení klientů pro nástroj System Center 2012 Configuration Manager](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>Poradce při potížích  
  
### <a name="log-file-locations"></a>Umístění souborů protokolu  
 Následující soubory protokolu jsou generována během instalace rozhraní .NET Framework:  
  
 %temp%\Microsoft rozhraní .NET framework *verze*\*.txt  
 %temp%\Microsoft rozhraní .NET framework *verze*\*.html  
  
 kde *verze* je verze rozhraní .NET Framework, který instalujete, jako je například 4.5 nebo 4.7.2.  
 
 Můžete také zadat adresář, do které protokolu soubory jsou zapsány pomocí `/log` možnost příkazového řádku v příkazu instalace rozhraní .NET Framework. Další informace najdete v tématu [rozhraní .NET Framework – Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md#command-line-options). 
 
 Můžete použít [nástroj kolekce protokol](https://www.microsoft.com/download/details.aspx?id=12493) shromažďovat soubory protokolů rozhraní .NET Framework a vytvořte soubor komprimovaný soubor CAB (.cab), která snižuje velikost souborů.  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>Návratové kódy  
 Následující tabulka uvádí nejběžnější návratové kódy z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable instalační program. Návratové kódy jsou stejné pro všechny verze instalačního programu.  
  
 Odkazy na podrobné informace naleznete v části Další [stáhnout kódy chyb](#additional_error_codes).  
  
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
  
-   [Kódy chyb Background Intelligent Transfer Service (BITS)](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [Adresa URL Přezdívka chybové kódy](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [Kódy chyb WinHttp](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 Další kódy chyb:  
  
-   [Kódy chyb Instalační služby systému Windows](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [Kódy výsledků agenta Windows Update Agent](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)
