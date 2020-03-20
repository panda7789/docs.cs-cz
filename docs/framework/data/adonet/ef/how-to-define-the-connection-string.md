---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150568"
---
# <a name="how-to-define-the-connection-string"></a>Postupy: Definování připojovacího řetězce

Toto téma ukazuje, jak definovat připojovací řetězec, který se používá při připojování ke konceptuálnímu modelu. Toto téma je založeno na konceptuálním modelu [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) AdventureWorks Prodejní model se používá v celé témata související s úkoly v dokumentaci entity framework. Toto téma předpokládá, že jste již nakonfigurovali entity framework a definovali obchodní model AdventureWorks. Další informace naleznete v [tématu How to: Manually Define the Model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Postupy v tomto tématu jsou také zahrnuty v [postupech: Ruční konfigurace projektu entity framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Pokud použijete Průvodce datovým modelem entity v projektu sady Visual Studio, automaticky vygeneruje soubor .edmx a nakonfiguruje projekt tak, aby používal rozhraní Entity Framework. Další informace naleznete v [tématu How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Definování připojovacího řetězce Entity Framework

- Otevřete konfigurační soubor aplikace projektu (app.config) a přidejte následující připojovací řetězec:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Pokud projekt nemá konfigurační soubor aplikace, můžete jej přidat tak, že z nabídky **Projekt** vyberete **Přidat novou položku,** vyberete kategorii **Obecné,** vyberete **Konfigurační soubor aplikace**a potom klepnete na tlačítko **Přidat**.

## <a name="see-also"></a>Viz také

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Postup: Vytvoření nového souboru .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [nástroje datového modelu ADO.NET entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
