---
title: Úvodní příručka (datové služby WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121216"
---
# <a name="quickstart-wcf-data-services"></a>Úvodní příručka (datové služby WCF)

Tento rychlý start vám pomůže seznámit se s datovými službami WCF a protokolem OData (Open Data Protocol) prostřednictvím řady úkolů, které podporují témata v [tématu Začínáme](getting-started-with-wcf-data-services.md).

## <a name="what-youll-learn"></a>Co se dozvíte

První úkol v tomto rychlém startu ukazuje, jak vytvořit datovou službu pro vystavení datového kanálu OData z ukázkové databáze Northwind. V pozdějších tématech budete přistupovat k informačnímu kanálu OData pomocí webového prohlížeče a také vytvoříte klientskou aplikaci WPF (Windows Presentation Foundation), která využívá informační kanál OData pomocí klientských knihoven.

## <a name="prerequisites"></a>Požadavky

Chcete-li tento rychlý start dokončit, nainstalujte následující součásti:

- Visual Studio

- Instance serveru SQL Server. To zahrnuje SQL Server Express, který je součástí výchozí instalace Visual Studio 2015 nebo jako součást **úlohy ukládání dat a zpracování** v sadě Visual Studio 2017 nebo novější.

- Ukázkovou databázi Northwind Chcete-li databázi nainstalovat, spusťte skript Transact-SQL z [ukázkových databází Northwind a pubs pro microsoft sql server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

## <a name="wcf-data-services-quickstart-tasks"></a>Úlohy rychlého spuštění datových služeb WCF

 [Vytvoření datové služby](creating-the-data-service.md)

 Definujte ASP.NET aplikaci, definujte datový model, vytvořte datovou službu a povolte přístup k prostředkům.

 [Přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Spusťte službu z aplikace Visual Studio a získejte přístup ke službě odesláním požadavků HTTP GET prostřednictvím webového prohlížeče do informačního kanálu.

 [Vytvoření klientské aplikace rozhraní .NET Framework](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 Vytvořte aplikaci WPF, která spotřebovává datový kanál OData, váže data s ovládacími prvky systému Windows, mění data v vázaných ovládacích prvcích a pak odešle změny zpět do datové služby.

> [!NOTE]
> Soubory projektu z dokončené verze rychlého startu lze stáhnout z [GitHubu](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Spuštění rychlého startu](creating-the-data-service.md)

## <a name="see-also"></a>Viz také

- [ADO.NET Entity Framework](../adonet/ef/index.md)
