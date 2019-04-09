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
ms.openlocfilehash: 0ff426f051b37830b0161cd0e0e4368a5750c664
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124764"
---
# <a name="deploying-the-net-framework-and-applications"></a>Nasazení .NET Framework a aplikací
Tento článek pomůže začít nasazení rozhraní .NET Framework s vaší aplikací. Většina informací je určená pro vývojáře, výrobci OEM a enterprise administrators. Uživatelé, kteří chtějí nainstalovat rozhraní .NET Framework na svých počítačích byste si přečíst [instalace rozhraní .NET Framework](~/docs/framework/install/index.md).  
  
## <a name="key-deployment-resources"></a>Klíče nasazení prostředků  
 Použijte následující odkazy na další témata MSDN pro konkrétní informace o nasazení a údržba rozhraní .NET Framework.  
  
 **Instalace a nasazení**  
  
-   Obecné informace Instalační program a nasazení:  
  
    -   Instalační program možnosti:  
  
        -   [Webová instalační služba](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [Offline instalační program](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   Režimy instalace:  
  
        -   [Bezobslužná instalace](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [Zobrazení uživatelského rozhraní](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   Nasazení rozhraní .NET Framework pomocí klientské aplikace (pro vývojáře):  
  
    -   [Pomocí programu InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení  
  
    -   [Pomocí aplikace Visual Studio ClickOnce](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [Vytvoření balíčku instalace WiX](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [Pomocí vlastního instalačního programu](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   [Další informace o](../../../docs/framework/deployment/deployment-guide-for-developers.md) pro vývojáře  
  
-   Nasazení rozhraní .NET Framework (pro výrobce OEM a správce):  
  
    -   [Windows Assessment and Deployment Kit (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [Příručka pro správce](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 **Údržba**  
  
-   Obecné informace najdete v tématu [blogu .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=254977)  
  
-   [Zjištění verze](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [Zjišťování aktualizací service Pack a aktualizace](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a>Funkce, které zjednodušují nasazení  
 Rozhraní .NET Framework poskytuje řadu základních funkcí, které zjednodušují nasazení aplikací:  
  
-   Aplikace bez dopadu.  
  
     Tato funkce zajišťuje izolaci aplikace a eliminuje DLL – konflikty. Ve výchozím nastavení komponenty nemají vliv na jiné aplikace.  
  
-   Součásti ve výchozím nastavení je privátní.  
  
     Ve výchozím nastavení komponenty jsou nasazené do adresáře aplikace a jsou viditelné pouze pro obsahující aplikaci.  
  
-   Řízené sdílení kódu.  
  
     Sdílení kódu, musíte explicitně zpřístupnit kód pro sdílení obsahu namísto výchozího chování.  
  
-   Správa verzí vedle sebe.  
  
     Více verzí aplikace nebo součásti mohou existovat vedle sebe, můžete zvolit, které verze používat, a modul common language runtime vynucuje zásad správy verzí.  
  
-   Replikace a nasazení XCOPY.  
  
     Samostatná a místním popisu komponent a aplikací můžete nasadit bez položky registru nebo závislosti.  
  
-   Na průběžné aktualizace.  
  
     Správci můžou použít hostitele, jako je ASP.NET, k aktualizaci aplikace knihovny DLL, i na vzdálených počítačích.  
  
-   Integrace pomocí Instalační služby systému Windows.  
  
     Oznámení o inzerovaném programu, publikování, opravy a instalaci na vyžádání jsou všechny dostupné při nasazování aplikace.  
  
-   Nasazení v podniku.  
  
     Tato funkce poskytuje distribuce snadno softwaru, včetně použití služby Active Directory.  
  
-   Stahování a ukládání do mezipaměti.  
  
     Přírůstková stahování zachovat menší soubory ke stažení a komponenty můžou být izolované pro použití pouze pomocí aplikace pro nasazení nízkým dopadem na koncové uživatele.  
  
-   Částečně důvěryhodným kódem.  
  
     Identita je založena na kódu, nikoli na uživatele a dialogová žádný certifikát.  
  
## <a name="packaging-and-distributing-net-framework-applications"></a>Balení a distribuce aplikací rozhraní .NET Framework  
 Některé balení a informace o nasazení pro rozhraní .NET Framework je popsané v dalších částech v dokumentaci. Tyto části obsahují informace o popisující samy sebe jednotky nazvané [sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), které vyžadují žádné položky registru [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), který zajistí jedinečnost názvu a zabránit název falšování identity, a [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md), které řeší celou řadu problémy související s DLL – konflikty. Následující části obsahují informace o balení a distribuce aplikací rozhraní .NET Framework.  
  
### <a name="packaging"></a>Balení  
 Rozhraní .NET Framework poskytuje následující možnosti pro vytváření balíčků aplikací:  
  
-   Jako jednoho sestavení nebo jako kolekci sestavení.  
  
     Když je tato možnost jednoduše používáte soubory .dll nebo .exe jako byly vytvořeny.  
  
-   Jako soubory CAB (CAB).  
  
     Pomocí této možnosti komprimovat soubor do souborů .cab distribuce nebo stáhnout méně časově náročné.  
  
-   Jako balíček Instalační služby systému Windows nebo v jiných formátů Instalační služby.  
  
     Pomocí této možnosti vytvoříte soubory .msi pro použití Instalační služby systému Windows nebo balíček aplikace pro použití s další instalační služby.  
  
### <a name="distribution"></a>Distribuce  
 Rozhraní .NET Framework poskytuje následující možnosti distribuce aplikací:  
  
-   Pomocí příkazu XCOPY nebo FTP.  
  
     Protože common language runtime aplikace jsou samovysvětlující a vyžadují žádné položky registru, jednoduše zkopírujte aplikaci do příslušného adresáře můžete použít příkazu XCOPY nebo FTP. Aplikace se dá spustit pak z tohoto adresáře.  
  
-   Použijte kód ke stažení.  
  
     Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikové síti, do počítače stáhnout kód a spusťte aplikaci existuje.  
  
-   Pomocí instalačního programu jako 2.0 Instalační služby systému Windows.  
  
     2.0 Instalační služby systému Windows můžete nainstalovat, opravit nebo odebrat sestavení rozhraní .NET Framework v globální mezipaměti sestavení a privátní adresáře.  
  
### <a name="installation-location"></a>Umístění instalace  
 Pokud chcete zjistit, jak nasadíte sestavení vaší aplikace, takže najdete modulem runtime, naleznete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Důležité informace o zabezpečení může také ovlivnit způsob nasazení vaší aplikace. Spravovaný kód podle toho, kde je kód umístěn udělují oprávnění zabezpečení. Nasazení aplikace nebo komponenty do umístění, ve kterém přijímá trochu vztahu důvěryhodnosti, jako je například Internet, omezení aplikace nebo komponenta přínosech. Další informace o nasazení a důležité informace o zabezpečení najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Popisuje, jak modul common language runtime určuje sestavení, které použít ke splnění požadavků vazby.|  
|[Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|Tento článek popisuje způsoby, jak se vyhnout problémům identity typu, který může mít za následek <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a další chyby.|  
|[Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md)|Popisuje správce restartování se zabránilo restartuje kdykoli je to možné a vysvětluje, jak aplikace, které instalace rozhraní .NET Framework můžete využívat jejich výhod.|  
|[Příručka nasazení pro administrátory](../../../docs/framework/deployment/guide-for-administrators.md)|Vysvětluje, jak může správce systému můžete nasadit rozhraní .NET Framework a jeho systémové závislosti napříč sítí pomocí System Center Configuration Manageru (SCCM).|  
|[Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)|Vysvětluje, jak vývojáři můžete nainstalovat rozhraní .NET Framework na jejich uživatele, počítače s jejich aplikacemi.|  
|[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)|Tento článek popisuje možnosti nasazení v sadě Visual Studio, včetně pokynů pro publikování aplikace pomocí technologie ClickOnce a instalační služby systému Windows.| 
|[Publikování aplikací ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Popisuje, jak zabalit aplikace modelu Windows Forms a nasazení pomocí technologie ClickOnce pro klientské počítače v síti.|  
|[Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|Popisuje model střed a paprsek, balení a nasazení prostředků; využívající rozhraní .NET Framework popisuje konvence, proces získávání náhradních a balení alternativy pojmenování prostředků.|  
|[Nasazení aplikace spolupráce](../../../docs/framework/interop/deploying-an-interop-application.md)|Vysvětluje způsob dodání a nainstalujte spolupráce – aplikace, které sestavení klienta rozhraní .NET Framework, obvykle zahrnují jeden nebo více sestavení vzájemné spolupráce reprezentující různé knihovny typů modelu COM, a jeden nebo víc registrovaných komponent COM.|  
|[Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Popisuje, jak spustit bez upozornění a sledovat proces instalace rozhraní .NET Framework při vlastním zobrazením průběhu instalace.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce vývojem](../../../docs/framework/development-guide.md)
