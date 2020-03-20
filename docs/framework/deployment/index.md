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
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716467"
---
# <a name="deploying-the-net-framework-and-applications"></a>Nasazení .NET Framework a aplikací

Tento článek vám pomůže začít nasazovat rozhraní .NET Framework s vaší aplikací. Většina informací je určena vývojářům, oemům oem a správcům rozlehlé sítě. Uživatelé, kteří chtějí nainstalovat rozhraní .NET Framework do svých počítačů, by si měli [přečíst článek Instalace rozhraní .NET Framework](../install/index.md).

## <a name="key-deployment-resources"></a>Klíčové prostředky pro nasazení

Konkrétní informace o nasazení a údržbě rozhraní .NET Framework použijte následující odkazy na jiná témata služby MSDN.

**Nastavení a nasazení**

- Obecné informace o instalačním programu a nasazení:

  - Možnosti instalačního programu:

    - [Webový instalační program](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Offline instalační program](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Instalační režimy:

    - [Bezobslužná instalace](deployment-guide-for-developers.md#chaining_custom)

    - [Zobrazení nového ui](deployment-guide-for-developers.md#chaining_default)

  - [Snížení restartování systému během instalace rozhraní .NET Framework 4.5](reducing-system-restarts.md)

  - [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- Nasazení rozhraní .NET Framework s klientskou aplikací (pro vývojáře):

  - [Použití programu InstallShield](deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení

  - [Použití aplikace Visual Studio ClickOnce](deployment-guide-for-developers.md#clickonce-deployment)

  - [Vytvoření instalačního balíčku WiX](deployment-guide-for-developers.md#wix)

  - [Použití vlastního instalačního programu](deployment-guide-for-developers.md#chaining)

  - [Další informace](deployment-guide-for-developers.md) pro vývojáře

- Nasazení rozhraní .NET Framework (pro oemy a správce):

  - [Sada Windows Assessment and Deployment Kit (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Průvodce správcem](guide-for-administrators.md)

**Údržba**

- Obecné informace naleznete na [blogu rozhraní .NET Framework](https://devblogs.microsoft.com/dotnet/).

- [Zjišťování verzí](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [Zjišťování aktualizací Service Pack a aktualizací](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Funkce, které zjednodušují nasazení

Rozhraní .NET Framework poskytuje řadu základních funkcí, které usnadňují nasazení aplikací:

- Aplikace bez dopadu.

     Tato funkce poskytuje izolaci aplikací a eliminuje konflikty dll. Ve výchozím nastavení součásti nemají vliv na jiné aplikace.

- Soukromé součásti ve výchozím nastavení.

     Ve výchozím nastavení jsou součásti nasazeny do adresáře aplikace a jsou viditelné pouze pro obsahující aplikaci.

- Řízené sdílení kódu.

     Sdílení kódu vyžaduje, abyste explicitně zpřístupnit kód pro sdílení namísto výchozí chování.

- Souběžná správa verzí.

     Více verzí komponenty nebo aplikace může existovat vedle sebe, můžete si vybrat, které verze se mají použít, a běžný jazyk runtime vynucuje zásady správy verzí.

- Nasazení a replikace XCOPY.

     Samostatné a samostatné součásti a aplikace lze nasadit bez položek registru nebo závislostí.

- Průběžně aktuální informace.

     Správci mohou k aktualizaci knihoven DLL programů, například ASP.NET, dokonce i ve vzdálených počítačích.

- Integrace s Instalační službou systému Windows.

     Reklama, publikování, opravy a instalace na vyžádání jsou k dispozici při nasazování aplikace.

- Podnikové nasazení.

     Tato funkce poskytuje snadnou distribuci softwaru, včetně použití služby Active Directory.

- Stahování a ukládání do mezipaměti.

     Přírůstkové stahování udržuje stahování menší a součásti mohou být izolovány pouze pro použití aplikací pro nasazení s nízkým dopadem.

- Částečně důvěryhodný kód.

     Identita je založena na kódu namísto uživatele a nezobrazí se žádná dialogová okna certifikátu.

## <a name="packaging-and-distributing-net-framework-applications"></a>Balení a distribuce aplikací rozhraní .NET Framework

Některé informace o balení a nasazení pro rozhraní .NET Framework jsou popsány v jiných částech dokumentace. Tyto oddíly obsahují informace o jednotkách s vlastním popisem [nazývaných sestavení](../../standard/assembly/index.md), které nevyžadují žádné položky registru, [sestavení se silným názvem](../../standard/assembly/strong-named.md), které zajišťují jedinečnost názvů a zabraňují falšování názvů, a [správu verzí sestavení](../../standard/assembly/versioning.md), které řeší mnoho problémů spojených s konflikty dll. Následující části obsahují informace o balení a distribuci aplikací rozhraní .NET Framework.

### <a name="packaging"></a>Balení

Rozhraní .NET Framework poskytuje následující možnosti pro balení aplikací:

- Jako jedno sestavení nebo jako kolekce sestavení.

     Pomocí této možnosti jednoduše použijete soubory DLL nebo EXE tak, jak byly vytvořeny.

- Jako skříň (CAB) soubory.

     Pomocí této možnosti můžete komprimovat soubory do souborů CAB, aby distribuce nebo stáhnout méně časově náročné.

- Jako balíček Instalační služby systému Windows nebo v jiných formátech instalačního programu.

     Pomocí této možnosti vytvoříte soubory MSI pro použití s Instalační službou systému Windows nebo zabalíte aplikaci pro použití s jiným instalačním programem.

### <a name="distribution"></a>Distribuce

Rozhraní .NET Framework poskytuje následující možnosti pro distribuci aplikací:

- Použijte XCOPY nebo FTP.

     Vzhledem k tomu, že aplikace s běžným jazykovým runtime jsou samoobslužné a nevyžadují žádné položky registru, můžete pomocí xcopy nebo FTP jednoduše zkopírovat aplikaci do příslušného adresáře. Aplikace pak lze spustit z tohoto adresáře.

- Použijte kód ke stažení.

     Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikové sítě intranet, můžete jednoduše stáhnout kód do počítače a spustit aplikaci tam.

- Použijte instalační program, například Instalační službu systému Windows 2.0.

     Instalační služba systému Windows 2.0 může instalovat, opravovat nebo odebírat sestavení rozhraní .NET Framework v globální mezipaměti sestavení a v soukromých adresářích.

### <a name="installation-location"></a>Umístění instalace

Chcete-li zjistit, kde nasadit sestavení aplikace tak, aby je bylo možné najít v době runtime, naleznete [v tématu Jak runtime vyhledá sestavení](how-the-runtime-locates-assemblies.md).

Důležité informace o zabezpečení může také ovlivnit způsob nasazení aplikace. Oprávnění zabezpečení jsou udělena spravovanému kódu podle toho, kde je kód umístěn. Nasazení aplikace nebo součásti do umístění, kde získá malou důvěryhodnost, například Internet, omezuje, co aplikace nebo součást může dělat. Další informace o nasazení a aspektech zabezpečení naleznete v [tématu Základy zabezpečení přístupu kódu](../misc/code-access-security-basics.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Jak běhové prostředí vyhledává sestavení](how-the-runtime-locates-assemblies.md)|Popisuje, jak běžný jazyk runtime určuje, které sestavení použít ke splnění požadavku na vazbu.|
|[Doporučené postupy pro načtení sestavení](best-practices-for-assembly-loading.md)|Popisuje způsoby, jak se vyhnout problémům <xref:System.InvalidCastException>s <xref:System.MissingMethodException>identitou typu, které mohou vést k , a dalším chybám.|
|[Omezení restartů systému při instalaci rozhraní .NET Framework 4.5](reducing-system-restarts.md)|Popisuje Správce restartování, který brání restartování, kdykoli je to možné, a vysvětluje, jak aplikace, které instalují rozhraní .NET Framework, mohou využít.|
|[Příručka nasazení pro administrátory](guide-for-administrators.md)|Vysvětluje, jak může správce systému nasadit rozhraní .NET Framework a jeho systémové závislosti v síti pomocí nástroje Microsoft Endpoint Configuration Manager.|
|[Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)|Vysvětluje, jak mohou vývojáři nainstalovat rozhraní .NET Framework do počítačů svých uživatelů pomocí svých aplikací.|
|[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)|Popisuje možnosti nasazení v sadě Visual Studio, včetně pokynů pro publikování aplikace pomocí technologií ClickOnce a Instalační služby systému Windows.|
|[Publikování aplikací ClickOnce](/visualstudio/deployment/publishing-clickonce-applications)|Popisuje, jak zabalit aplikaci Windows Forms a nasadit ji pomocí clickonce do klientských počítačů v síti.|
|[Zabalení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|Popisuje model rozbočovače a paprsku, který rozhraní .NET Framework používá k balení a nasazení prostředků. zahrnuje konvence pojmenování prostředků, záložní proces a alternativy balení.|
|[Nasazení aplikace spolupráce](../interop/deploying-an-interop-application.md)|Vysvětluje, jak dodávat a instalovat interop aplikace, které obvykle zahrnují sestavení klienta rozhraní .NET Framework, jedno nebo více meziop sestavení představujících odlišné knihovny typů MODELU A jednu nebo více registrovaných součástí modelu COM.|
|[Postupy: Získání procesu z instalačního programu .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)|Popisuje, jak tiše spustit a sledovat proces nastavení rozhraní .NET Framework při zobrazení vlastního zobrazení průběhu instalace.|

## <a name="see-also"></a>Viz také

- [Průvodce vývojem](../development-guide.md)
