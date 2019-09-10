---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854655"
---
# <a name="how-to-define-the-connection-string"></a>Postupy: Definování připojovacího řetězce

Toto téma ukazuje, jak definovat připojovací řetězec, který se používá při připojování k koncepčnímu modelu. Toto téma je založené na modelu [AdventureWorks Sales](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) koncepční model. Model prodeje společnosti AdventureWorks se používá v různých tématech souvisejících s úlohami v dokumentaci k Entity Framework. Toto téma předpokládá, že jste již nakonfigurovali Entity Framework a definovali prodejní model AdventureWorks. Další informace najdete v tématu [jak: Ručně definujte model a mapovací soubory](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Postupy v tomto tématu jsou také zahrnuty v [tématu Postupy: Ručně nakonfigurujte Entity Framework projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Použijete-li průvodce model EDM (Entity Data Model) v projektu sady Visual Studio, automaticky vygeneruje soubor. edmx a nakonfiguruje projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použití Průvodce model EDM (Entity Data Model)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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
- [Postupy: Vytvořit nový soubor. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
