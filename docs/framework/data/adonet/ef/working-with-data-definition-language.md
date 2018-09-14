---
title: Práce s jazyk pro definování dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 25d7f49644996d87ddb5d191dc313916c0ca6fbb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594708"
---
# <a name="working-with-data-definition-language"></a>Práce s jazyk pro definování dat
Počínaje [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] verze 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje jazyk pro definování dat (DDL). To umožňuje vytvořit nebo odstranit instanci databáze na základě připojovacího řetězce a metadata modelu úložiště (SSDL).  
  
 Následující metody u <xref:System.Data.Objects.ObjectContext> můžete provádět následující připojovací řetězec a obsah souborů SSDL: vytvoření nebo odstranění databáze, zkontrolujte, jestli databáze existuje a zobrazit vygenerovaný skript jazyka DDL:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  Provádění příkazů DDL předpokládá dostatečná oprávnění.  
  
 Výše uvedených metod delegáta většinu práce, kterou podkladového zprostředkovatele dat ADO.NET. Je poskytovatele povinností ujistit se, že zásady vytváření názvů sloužící ke generování databázové objekty je v souladu s konvencemi použitými pro dotazování a aktualizace.  
  
 Následující příklad ukazuje, jak vytvořit databázi na základě existující modelu. Také přidá nový objekt entity v kontextu objektu a uloží jej do databáze.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Chcete-li definovat databáze založené na existující model  
  
1.  Vytvořte konzolovou aplikaci.  
  
2.  Přidáte existující model pro vaši aplikaci.  
  
    1.  Přidat prázdný model s názvem `SchoolModel`. Pokud chcete vytvořit prázdný model, najdete v článku [postupy: vytvoření nové edmx soubor](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) tématu.  
  
     Soubor SchoolModel.edmx je přidán do projektu.  
  
    1.  Zkopírujte koncepční, úložiště a mapování obsahu pro model školní ze [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) tématu.  
  
    2.  Otevřete soubor SchoolModel.edmx a vložte obsah v rámci `edmx:Runtime` značky.  
  
3.  Přidejte následující kód do hlavní funkce. Kód inicializuje řetězec připojení k vašemu databázovému serveru, zobrazení skriptu jazyka DDL, vytvoří databázi, přidá nové entity v kontextu a uloží změny do databáze.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
