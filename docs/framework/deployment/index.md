---
title: Nasazení .NET Framework a aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2686d0db966192606656167d6e505f34ded333f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-the-net-framework-and-applications"></a>Nasazení .NET Framework a aplikací
Tento článek pomáhá začít pracovat, nasazení rozhraní .NET Framework s vaší aplikací. Většinu informací je určený pro vývojáře, výrobci OEM a správcům. Přečtěte si uživatelé, kteří chtějí nainstalovat rozhraní .NET Framework na svých počítačích [instalace rozhraní .NET Framework](~/docs/framework/install/index.md).  
  
## <a name="key-deployment-resources"></a>Klíče nasazení prostředků  
 Pomocí následujících odkazů na další témata MSDN pro konkrétní informace o nasazení a obsluhy rozhraní .NET Framework.  
  
 **Instalace a nasazení**  
  
-   Obecné informace Instalační program a nasazení:  
  
    -   Instalační program možnosti:  
  
        -   [Instalační program webové](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [Offline instalační program](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   Režimy instalace:  
  
        -   [Bezobslužná instalace](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [Zobrazení uživatelského rozhraní](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   Nasazení rozhraní .NET Framework s klientskou aplikaci (pro vývojáře):  
  
    -   [Pomocí InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení  
  
    -   [Pomocí aplikace Visual Studio ClickOnce](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [Vytváření WiX instalace balíčku](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [Použití vlastní instalační program](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   [Další informace o](../../../docs/framework/deployment/deployment-guide-for-developers.md) pro vývojáře  
  
-   Nasazení .NET Framework (pro výrobce OEM a správci):  
  
    -   [Sada Windows Assessment and Deployment Kit (ADK)](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [Příručka pro správce](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 **Údržba**  
  
-   Obecné informace najdete v tématu [blog rozhraní .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=254977)  
  
-   [Zjišťování verze](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [Zjišťování aktualizací service Pack a aktualizace](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a>Funkce, které zjednodušují nasazení  
 Rozhraní .NET Framework poskytuje celou řadu základních funkcí, které usnadňují nasazení aplikací:  
  
-   Aplikace bez dopadu.  
  
     Tato funkce poskytuje izolace aplikací a eliminuje DLL – konflikty. Ve výchozím nastavení součásti nemají vliv na ostatní aplikace.  
  
-   Privátní součásti ve výchozím nastavení.  
  
     Ve výchozím nastavení součásti jsou nasazeny do adresáře aplikace a jsou viditelné pouze pro obsahující aplikaci.  
  
-   Sdílení řízené kódu.  
  
     Sdílení kódu vyžaduje, abyste výslovně zpřístupnit kód pro sdílení namísto výchozí chování.  
  
-   Správa verzí vedle sebe.  
  
     Více verzí součást nebo aplikace, mohou existovat vedle sebe, můžete používat jaké verze a modul common language runtime vynucuje zásady správy verzí.  
  
-   XCOPY nasazení a replikace.  
  
     Samoobslužné popsané a samostatné součásti a aplikace můžete nasadit bez položky registru nebo závislosti.  
  
-   Na průběžně aktualizuje.  
  
     Správci můžou pomocí hostitele, jako je ASP.NET, aktualizujte program knihovny DLL, i na vzdálených počítačích.  
  
-   Integrace s Instalační služby systému Windows.  
  
     Oznámení o inzerovaném programu, publikování, opravy a instalaci na vyžádání jsou všechny dostupné při nasazení aplikace.  
  
-   Podnikové nasazení.  
  
     Tato funkce poskytuje distribuce snadno softwaru, včetně použití služby Active Directory.  
  
-   Stahování a ukládání do mezipaměti.  
  
     Přírůstkové stahování ponechte menší stahování a může být součástí izolované pro použití pouze pomocí aplikace pro nasazení nízká dopad.  
  
-   Částečně důvěryhodný kód.  
  
     Identity je založený na kód, nikoli na uživatele a zobrazí se dialogová žádný certifikát.  
  
## <a name="packaging-and-distributing-net-framework-applications"></a>Balení a distribuce aplikací rozhraní .NET Framework  
 Některé balení a informace o nasazení pro rozhraní .NET Framework je popsané v dalších částech v dokumentaci. Tyto části obsahují informace o popisující samy sebe jednotek nazývaných [sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), které vyžadují žádné položky registru [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), což zajistí název jedinečnost a zabránit název falšování identity, a [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md), které řeší mnohé z problémů spojených s DLL – konflikty. Následující části obsahují informace o balení a distribuce aplikací rozhraní .NET Framework.  
  
### <a name="packaging"></a>Balení  
 Rozhraní .NET Framework poskytuje následující možnosti pro vytváření balíčků aplikací:  
  
-   Jako jednoho sestavení nebo jako kolekce sestavení.  
  
     Pomocí této možnosti můžete jednoduše použijte soubory .dll nebo .exe jako jejich byly vytvořené.  
  
-   Jako soubory CAB (CAB).  
  
     Pomocí této možnosti komprimovat soubor do souborů .cab distribuce stát nebo stáhnout časově méně náročné.  
  
-   Jako balíček Instalační služby systému Windows nebo v dalších formátech Instalační služby.  
  
     Pomocí této možnosti vytvoříte soubory s příponou MSI pro použití s Instalační služby systému Windows nebo balíček aplikace pro použití s další instalační služby.  
  
### <a name="distribution"></a>Distribuce  
 Rozhraní .NET Framework poskytuje následující možnosti pro distribuci aplikací:  
  
-   Pomocí příkazu XCOPY nebo FTP.  
  
     Protože běžné aplikace runtime jazyka jsou popisující samy sebe a nevyžadují žádné položky registru, můžete použít příkaz XCOPY nebo FTP jednoduše zkopírovat aplikaci do příslušného adresáře. Aplikace pak spustíte z tohoto adresáře.  
  
-   Pomocí kódu stahování.  
  
     Při distribuci aplikace přes Internet nebo prostřednictvím podnikovém intranetu, do počítače stáhnout kód a spusťte aplikaci existuje.  
  
-   Pomocí instalačního programu například systému Windows verze 2.0.  
  
     2.0 Instalační služby systému Windows můžete nainstalovat, opravit nebo odebrat sestavení rozhraní .NET Framework v globální mezipaměti sestavení a privátní adresáře.  
  
### <a name="installation-location"></a>Umístění instalace  
 Chcete-li zjistit, kde nasadit sestavení vaší aplikace, takže naleznete modulem runtime, přečtěte si téma [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Aspekty zabezpečení může ovlivnit také nasazení vaší aplikace. Jsou udělena oprávnění zabezpečení pro spravovaný kód podle kde se nachází kódu. Nasazení aplikace nebo součásti do umístění, kde obdrží málo vztahu důvěryhodnosti, jako je Internet, limity co aplikací nebo součástí můžete provést. Další informace o nasazení a aspekty zabezpečení najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Popisuje, jak modul common language runtime určuje sestavení, které použít ke splnění požadavku vazby.|  
|[Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|Popisuje způsoby, kterými se chcete vyhnout potížím typ identity, který může vést k <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a dalších chyb.|  
|[Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)|Popisuje správce restartovat, aby se zabránilo restartuje, pokud je to možné a vysvětluje, jak aplikace, které instalaci rozhraní .NET Framework, můžete využít výhod ho.|  
|[Příručka nasazení pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md)|Vysvětluje, jak správce systému můžete nasadit rozhraní .NET Framework a jeho závislé součásti systému přes síť pomocí System Center Configuration Manager (SCCM).|  
|[Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)|Vysvětluje, jak vývojáři můžete nainstalovat rozhraní .NET Framework na své uživatele, počítače s aplikací.|  
|[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)|Popisuje možnosti nasazení v sadě Visual Studio, včetně pokynů pro publikování aplikace pomocí technologie ClickOnce a instalační služba systému Windows.| 
|[Publikování aplikací ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Popisuje, jak chcete balíček aplikace Windows Forms a nasaďte ho s ClickOnce do klientských počítačů v síti.|  
|[Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|Popisuje hvězdicové model, který používá rozhraní .NET Framework pro zabalení a nasazení prostředků; popisuje konvence, nouzové procesy a balení alternativních názvů prostředků.|  
|[Nasazení aplikace spolupráce](../../../docs/framework/interop/deploying-an-interop-application.md)|Vysvětluje, jak dodávat a nainstalujte zprostředkovatele komunikace s objekty aplikace, které obvykle obsahují sestavení klienta .NET Framework, jeden nebo více sestavení vzájemné spolupráce představující odlišné knihovny typů modelu COM, a jedna nebo více komponent COM registrované.|  
|[Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Popisuje, jak bezobslužná spustit a sledovat proces instalace rozhraní .NET Framework při zobrazování zobrazení průběh instalačního programu.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce vývojem](../../../docs/framework/development-guide.md)
