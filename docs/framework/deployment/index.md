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
ms.openlocfilehash: 04cbfb8d41135b57c3e090959e041f95fcda2840
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975682"
---
# <a name="deploying-the-net-framework-and-applications"></a>Nasazení .NET Framework a aplikací

Tento článek vám pomůže začít s nasazením .NET Framework s vaší aplikací. Většina informací je určená vývojářům, výrobcům OEM a podnikovým správcům. Uživatelé, kteří chtějí instalovat .NET Framework na svých počítačích, by si měli přečíst [instalaci .NET Framework](../install/index.md).

## <a name="key-deployment-resources"></a>Prostředky nasazení klíčů

Pro konkrétní informace o nasazení a údržbě .NET Framework použijte následující odkazy na další témata MSDN.

**Nastavení a nasazení**

- Obecné informace o instalačním programu a nasazení:

  - Možnosti instalačního programu:

    - [Webová instalační služba](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Offline instalační program](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Režimy instalace:

    - [Tichá instalace](deployment-guide-for-developers.md#chaining_custom)

    - [Zobrazení uživatelského rozhraní](deployment-guide-for-developers.md#chaining_default)

  - [Snížení restartu systému během instalací .NET Framework 4,5](reducing-system-restarts.md)

  - [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- Nasazení .NET Framework pomocí klientské aplikace (pro vývojáře):

  - [Používání programu InstallShield](deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení

  - [Použití aplikace Visual Studio ClickOnce](deployment-guide-for-developers.md#clickonce-deployment)

  - [Vytvoření instalačního balíčku WiX](deployment-guide-for-developers.md#wix)

  - [Použití vlastního instalačního programu](deployment-guide-for-developers.md#chaining)

  - [Další informace](deployment-guide-for-developers.md) pro vývojáře

- Nasazení .NET Framework (pro výrobce OEM a správce):

  - [Sada Windows Assessment and Deployment Kit (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Příručka pro správce](guide-for-administrators.md)

**Údržba**

- Obecné informace najdete na [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).

- [Zjišťují se verze](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [Zjišťování aktualizací Service Pack a aktualizací](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Funkce, které zjednodušují nasazení

.NET Framework poskytuje řadu základních funkcí, které usnadňují nasazení aplikací:

- Aplikace bez dopadu.

     Tato funkce poskytuje izolaci aplikace a eliminuje konflikty knihoven DLL. Ve výchozím nastavení komponenty neovlivňují jiné aplikace.

- Ve výchozím nastavení soukromé součásti.

     Ve výchozím nastavení jsou komponenty nasazeny do adresáře aplikace a jsou viditelné pouze pro aplikaci, která ji obsahuje.

- Řízená sdílení kódu.

     Sdílení kódu vyžaduje explicitní zpřístupnění kódu pro sdílení namísto výchozího chování.

- Souběžná Správa verzí.

     Několik verzí komponenty nebo aplikace může existovat současně, můžete zvolit, které verze se mají použít, a modul CLR (Common Language Runtime) vynutil zásady správy verzí.

- Nasazení a replikace XCOPY.

     Samostatné a samostatně uzavřené komponenty a aplikace lze nasadit bez položek registru nebo závislostí.

- Průběžné aktualizace.

     Správci můžou použít hostitele, jako je ASP.NET, k aktualizaci knihoven DLL programu, i na vzdálených počítačích.

- Integrace s Instalační služba systému Windows.

     Inzerce, publikování, opravy a instalace na vyžádání jsou dostupné při nasazení aplikace.

- Podnikové nasazení.

     Tato funkce poskytuje jednoduchou distribuci softwaru, včetně používání služby Active Directory.

- Stahování a ukládání do mezipaměti.

     Přírůstkové stahování udržuje menší soubory ke stažení a součásti lze izolovat pouze pro použití v aplikaci pro nasazení s nízkým dopadem.

- Částečně důvěryhodný kód.

     Identita je založena na kódu namísto uživatele a nezobrazují se dialogová okna certifikátu.

## <a name="packaging-and-distributing-net-framework-applications"></a>Balení a distribuce .NET Frameworkch aplikací

Některé informace o balení a nasazení pro .NET Framework jsou popsány v dalších částech dokumentace. Tyto části poskytují informace o jednotkách, které jsou označovány jako [sestavení](../../standard/assembly/index.md), které nevyžadují žádné položky registru, [sestavení se silným názvem](../../standard/assembly/strong-named.md), které zajišťují jedinečnost názvu a brání falšování názvů a [správu verzí sestavení](../../standard/assembly/versioning.md), které řeší mnohé problémy spojené s konflikty knihoven DLL. Následující části obsahují informace o balení a distribuci .NET Frameworkch aplikací.

### <a name="packaging"></a>Balení

.NET Framework poskytuje následující možnosti pro vytváření balíčků aplikací:

- Jako jedno sestavení nebo jako kolekce sestavení.

     Pomocí této možnosti jednoduše použijete soubory. dll nebo. exe, jak byly sestaveny.

- Jako soubory CAB.

     Pomocí této možnosti zkomprimujete soubory do souborů. cab, abyste mohli distribuovat nebo stahovat méně času náročného.

- Jako balíček Instalační služba systému Windows nebo v jiných formátech instalačního programu.

     Pomocí této možnosti vytvoříte soubory. msi pro použití s Instalační služba systému Windows nebo zabalíte aplikaci pro použití s nějakým jiným instalačním programem.

### <a name="distribution"></a>Šíření

.NET Framework poskytuje následující možnosti pro distribuci aplikací:

- Použijte XCOPY nebo FTP.

     Vzhledem k tomu, že aplikace modulu CLR (Common Language Runtime) samy popisují a nevyžadují žádné položky registru, můžete pomocí příkazu XCOPY nebo FTP jednoduše zkopírovat aplikaci do příslušného adresáře. Aplikaci lze následně spustit z tohoto adresáře.

- Použijte stahování kódu.

     Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikového intranetu, můžete jednoduše stáhnout kód do počítače a spustit aplikaci.

- Použijte instalační program, například Instalační služba systému Windows 2,0.

     Instalační služba systému Windows 2,0 může instalovat, opravovat nebo odebírat .NET Framework sestavení v globální mezipaměti sestavení (GAC) a v privátních adresářích.

### <a name="installation-location"></a>Umístění instalace

Chcete-li určit, kam se mají nasadit sestavení vaší aplikace, aby je bylo možné najít modulem runtime, přečtěte si téma [jak modul runtime vyhledává sestavení](how-the-runtime-locates-assemblies.md).

Požadavky na zabezpečení mohou také ovlivnit způsob nasazení aplikace. Oprávnění zabezpečení se udělují spravovanému kódu podle toho, kde se nachází kód. Nasazení aplikace nebo komponenty do umístění, kde obdrží malý vztah důvěryhodnosti, jako je například Internet, omezuje, co může aplikace nebo komponenta dělat. Další informace o možnostech nasazení a zabezpečení najdete v tématu [Základy zabezpečení přístupu kódu](../misc/code-access-security-basics.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Jak běhové prostředí vyhledává sestavení](how-the-runtime-locates-assemblies.md)|Popisuje, jak modul CLR (Common Language Runtime) určuje, které sestavení se má použít ke splnění požadavku vazby.|
|[Doporučené postupy pro načtení sestavení](best-practices-for-assembly-loading.md)|Popisuje způsoby, jak zabránit problémům s typem identity, který může vést k <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a dalším chybám.|
|[Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](reducing-system-restarts.md)|Popisuje správce restartování, který znemožňuje restartování, kdykoli je to možné, a vysvětluje, jak můžou aplikace, které instalují .NET Framework, využít.|
|[Příručka nasazení pro administrátory](guide-for-administrators.md)|Vysvětluje, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti pomocí System Center Configuration Manager (SCCM).|
|[Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)|Vysvětluje, jak můžou vývojáři instalovat .NET Framework na počítačích uživatelů s jejich aplikacemi.|
|[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)|Popisuje možnosti nasazení v aplikaci Visual Studio, včetně pokynů pro publikování aplikace pomocí technologie ClickOnce a Instalační služba systému Windows.|
|[Publikování aplikací ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Popisuje, jak zabalit aplikaci model Windows Forms a nasadit ji pomocí technologie ClickOnce na klientské počítače v síti.|
|[Zabalení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|Popisuje model hvězdicové a paprsky, které .NET Framework používá k zabalení a nasazení prostředků. Popisuje zásady vytváření názvů prostředků, záložní proces a alternativy balení.|
|[Nasazení aplikace spolupráce](../interop/deploying-an-interop-application.md)|Vysvětluje, jak dodávat a instalovat aplikace spolupráce, které obvykle zahrnují .NET Framework sestavení klienta, jedno nebo více definičních sestavení představujících odlišné knihovny typů modelu COM a jednu nebo více registrovaných komponent modelu COM.|
|[Postupy: Získání procesu z instalačního programu .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)|V této části najdete popis postupu při tichém spuštění a sledování procesu instalace .NET Framework při zobrazení vlastního zobrazení průběhu instalace.|

## <a name="see-also"></a>Viz také:

- [Průvodce vývojem](../development-guide.md)
