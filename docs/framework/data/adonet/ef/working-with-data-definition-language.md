---
title: Práce s jazykem DDL (Data Description Language)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: da37dc2ff08f127e17cd4e6f7cbeab88f2c8d5e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583446"
---
# <a name="working-with-data-definition-language"></a>Práce s jazykem DDL (Data Description Language)
Od verze rozhraní .NET Framework verze 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje jazyk pro definování dat (DDL). To umožňuje vytvořit nebo odstranit instanci databáze na základě připojovacího řetězce a metadata modelu úložiště (SSDL).  
  
 Následující metody u <xref:System.Data.Objects.ObjectContext> můžete provádět následující připojovací řetězec a obsah souborů SSDL: vytvoření nebo odstranění databáze, zkontrolujte, jestli databáze existuje a zobrazit vygenerovaný skript jazyka DDL:  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  Provádění příkazů DDL předpokládá dostatečná oprávnění.  
  
 Výše uvedených metod delegáta většinu práce, kterou podkladového zprostředkovatele dat ADO.NET. Je poskytovatele povinností ujistit se, že zásady vytváření názvů sloužící ke generování databázové objekty je v souladu s konvencemi použitými pro dotazování a aktualizace.  
  
 Následující příklad ukazuje, jak vytvořit databázi na základě existující modelu. Také přidá nový objekt entity v kontextu objektu a uloží jej do databáze.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Chcete-li definovat databáze založené na existující model  
  
1. Vytvořte konzolovou aplikaci.  
  
2. Přidáte existující model pro vaši aplikaci.  
  
    1. Přidat prázdný model s názvem `SchoolModel`. Chcete-li vytvořit prázdný model, najdete v článku [jak: Vytvořit nový edmx soubor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) tématu.  
  
     Soubor SchoolModel.edmx je přidán do projektu.  
  
    1. Zkopírujte koncepční, úložiště a mapování obsahu pro model školní ze [školní modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) tématu.  
  
    2. Otevřete soubor SchoolModel.edmx a vložte obsah v rámci `edmx:Runtime` značky.  
  
3. Přidejte následující kód do hlavní funkce. Kód inicializuje řetězec připojení k vašemu databázovému serveru, zobrazení skriptu jazyka DDL, vytvoří databázi, přidá nové entity v kontextu a uloží změny do databáze.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
