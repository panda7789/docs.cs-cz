---
title: 'Postupy: definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833955"
---
# <a name="how-to-define-the-connection-string"></a>Postupy: definování připojovacího řetězce

Toto téma ukazuje, jak definovat připojovací řetězec, který se používá při připojování k koncepčnímu modelu. Toto téma je založené na modelu [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) koncepční model. Model prodeje společnosti AdventureWorks se používá v různých tématech souvisejících s úlohami v dokumentaci k Entity Framework. Toto téma předpokládá, že jste již nakonfigurovali Entity Framework a definovali prodejní model AdventureWorks. Další informace naleznete v tématu [How to: Manual model and Mapping Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Postupy v tomto tématu jsou také zahrnuty v tématu [Postupy: ruční konfigurace entity Frameworkho projektu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Použijete-li průvodce model EDM (Entity Data Model) v projektu sady Visual Studio, automaticky vygeneruje soubor. edmx a nakonfiguruje projekt tak, aby používal Entity Framework. Další informace naleznete v tématu [How to: use the model EDM (Entity Data Model) Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Definování připojovacího řetězce Entity Framework

- Otevřete konfigurační soubor aplikace projektu (App. config) a přidejte následující připojovací řetězec:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Pokud projekt nemá konfigurační soubor aplikace, můžete jej přidat výběrem možnosti **Přidat novou položku** z nabídky **projekt** , výběrem kategorie **Obecné** , výběrem **konfiguračního souboru aplikace**a následným kliknutím na **Přidat**.

## <a name="see-also"></a>Viz také:

- [Rychlý start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Postupy: vytvoření nového souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
