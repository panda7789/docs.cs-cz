---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 8386f93d0e80aa824b1e91a130812b9b3a2b3619
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306388"
---
# <a name="how-to-define-the-connection-string"></a>Postupy: Definování připojovacího řetězce

Toto téma ukazuje, jak definovat připojovací řetězec, který je použit při připojování ke konceptuálního modelu. Toto téma vychází [AdventureWorks prodeje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) koncepčního modelu. AdventureWorks Sales Model se používá v tématech souvisejících s úlohami v rámci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci. Toto téma předpokládá, že jste již nakonfigurovali [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a definovaný Model prodeje AdventureWorks. Další informace najdete v tématu [jak: Ručně definovat modelu a mapování souborů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Postupy v tomto tématu jsou taky součástí [jak: Ruční konfigurace projektu v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Pokud používáte Průvodce datovým modelem Entity v projektu sady Visual Studio, automaticky vygeneruje soubor .edmx a nakonfiguruje projekt na používání [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Použití Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

## <a name="to-define-the-entity-framework-connection-string"></a>K definování připojovacího řetězce Entity Framework

- Otevřete konfigurační soubor projektu aplikace (app.config) a přidejte následující připojovací řetězec:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Pokud váš projekt nemá konfiguračního souboru aplikace, můžete výběrem možnosti Přidat **přidat novou položku** z **projektu** nabídce vyberete **Obecné** kategorie, Výběr **konfiguračního souboru aplikace**a pak levým na **přidat**.

## <a name="see-also"></a>Viz také:

- [Rychlý start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Postupy: Vytvoření nového souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
