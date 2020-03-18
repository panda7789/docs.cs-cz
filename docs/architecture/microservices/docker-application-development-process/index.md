---
title: Proces vývoje aplikací založených na Dockeru
description: Získejte přehled na vysoké úrovni o možnostech vývoje aplikací založených na Dockeru. Použití vašeho výběru Visual Studia pro Windows, Visual Studio pro Mac nebo Visual Studio Code pro podporu multiplatformní (Windows, macOS a Linux).
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77502722"
---
# <a name="development-process-for-docker-based-applications"></a>Proces vývoje aplikací založených na Dockeru

*Vyvíjejte kontejnerizované aplikace .NET tak, jak se vám líbí, buď integrované vývojové prostředí (IDE) zaměřené s Visual Studio a Visual Studio nástroje pro Docker nebo CLI/Editor zaměřené s Docker CLI a Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

### <a name="development-tool-choices-ide-or-editor"></a>Volby vývojových nástrojů: IDE nebo editor

Ať už dáváte přednost úplné a výkonné Rozhraní IDE nebo lehký a agilní editor, Microsoft má nástroje, které můžete použít pro vývoj aplikací Dockeru.

**Visual Studio (pro Windows).** Vývoj aplikací .NET Core 3.1 založených na Dockeru s Visual Studio vyžaduje Visual Studio 2019 verze 16.4 nebo novější. Visual Studio 2019 je dodáván s nástroji pro Docker již vestavěný. Nástroje pro Docker umožňují vyvíjet, spouštět a ověřovat vaše aplikace přímo v cílovém prostředí Dockeru. Stisknutím klávesy F5 můžete spustit a ladit aplikaci (jeden kontejner nebo více kontejnerů) přímo do hostitele Dockeru nebo stisknutím kombinace kláves CTRL+F5 upravit a aktualizovat aplikaci bez nutnosti znovu sestavit kontejner. Toto je nejvýkonnější volba vývoje pro aplikace založené na Dockeru.

**Visual Studio pro Mac.** Je to IDE, evoluce Xamarin Studio, běžící v macOS. Pro vývoj rozhraní .NET Core 3.1 vyžaduje verzi 8.4 nebo novější. To by měla být upřednostňovaná volba pro vývojáře pracující v počítačích macOS, kteří také chtějí používat výkonné ide.

**Visual Studio kód a Docker CLI**. Pokud dáváte přednost lehký a cross-platformní editor, který podporuje jakýkoli jazyk vývoje, můžete použít Visual Studio Code a Docker CLI. Jedná se o vývojový přístup napříč platformami pro macOS, Linux a Windows. Visual Studio Code navíc podporuje rozšíření pro Docker, jako je IntelliSense pro Dockerfiles a zkrácené úlohy pro spuštění příkazů Dockeru z editoru.

Instalací [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community)můžete použít jeden Docker CLI k vytváření aplikací pro Windows i Linux.

### <a name="additional-resources"></a>Další zdroje

- Sadu **Visual Studio**. Oficiální stránky. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio kód**. Oficiální stránky. \
  <https://code.visualstudio.com/download>

- **Desktop Dockeru pro windows community edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Docker Desktop pro Mac Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Jazyky a architektury .NET pro kontejnery Dockeru

Jak je uvedeno v předchozích částech této příručky, můžete použít rozhraní .NET Framework, .NET Core nebo open source Mono project při vývoji kontejnerizovaných aplikací .NET dockeru. Můžete vyvíjet\#v\#Jazyce C , F nebo Visual Basic při cílení Linux nebo Windows kontejnery, v závislosti na rozhraní .NET framework se používá. Další podrobnosti about.NET jazycích najdete v příspěvku blogu [Jazyková strategie .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Předchozí](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[další](docker-app-development-workflow.md)
