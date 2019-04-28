---
title: Identita objektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 0f1b6cf27101c2a7f55757b72b56b2291198404d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767534"
---
# <a name="object-identity"></a>Identita objektu
Objekty v modulu runtime mají jedinečné identity. Dvě proměnné, které odkazují na stejný objekt ve skutečnosti odkazovat na stejnou instanci objektu. Z tohoto důvodu jsou okamžitě viditelné prostřednictvím druhé změny, které provedete mimo jiné cestě prostřednictvím jedné proměnné.  
  
 Řádky v tabulce relační databáze nemají jedinečné identity. Protože každý řádek obsahuje jedinečné primární klíč, žádné dva řádky sdílet stejnou hodnotu klíče. Tato skutečnost však omezuje pouze obsah databázové tabulky.  
  
 Ve skutečnosti se nejčastěji přenesou data z databáze a na jinou úroveň, kde aplikace funguje s ním. Jedná se o model, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje. Až se přenesou data z databáze jako řádky, budete mít žádné očekává, že dva řádky, které představují stejná data ve skutečnosti odpovídají na stejný řádek instance. Když odešlete dotaz pro konkrétního zákazníka dvakrát, dostanete dva řádky dat. Každý řádek obsahuje stejné informace.  
  
 S objekty očekáváte, že něco velmi odlišné. Můžete očekávat, že po zadání otázky <xref:System.Data.Linq.DataContext> stejné informace opakovaně, ve skutečnosti poskytne vám stejná instance objektu. Toto chování očekávalo, protože objekty mají zvláštní význam pro vaši aplikaci a očekáváte, že aby se chovají jako objekty. Je navržena jako hierarchie nebo grafy. Očekáváte, že je jako taková načítat a nechcete dostávat myriády replikovaných instancí pouze z důvodu požádán o stejnou věc více než jednou.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.DataContext> spravuje identity objektu. Pokaždé, když je nový řádek načíst z databáze, řádku je zaznamenána v tabulce identity podle jeho primární klíč a je vytvořen nový objekt. Při každém načtení stejného řádku původní instance objektu bude předán zpět do aplikace. Tímto způsobem <xref:System.Data.Linq.DataContext> převádí koncept identity jak je vidět v databázi (to znamená, že primární klíče) na konceptu identity vidět jazyka (instance). Aplikace se zobrazují pouze objekt ve stavu, nejprve se načetla. Nová data, pokud se liší, je ignorována. Další informace najdete v tématu [načítání objektů z mezipaměti identit](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tento přístup se používá ke správě integrita místní objekty aby bylo možné podporovat optimistické aktualizace. Protože pouze změny, ke kterým dochází po při prvním vytvoření objektu jsou od aplikací, je záměr aplikace vymazat. Pokud mezitím došlo změny mimo stranou, jsou identifikované v době `SubmitChanges()` je volána.  
  
> [!NOTE]
>  Pokud se objekt požadoval dotaz jednoduše rozpoznatelným názvem jako jedna již načten, je proveden žádný dotaz. Tabulka identity funguje jako mezipaměť všech dříve načíst objekty.  
  
## <a name="examples"></a>Příklady  
  
### <a name="object-caching-example-1"></a>Objekt ukládání do mezipaměti – Příklad 1  
 V tomto příkladu Pokud stejný dotaz spustíte dvakrát, zobrazí se odkaz na stejný objekt v paměti pokaždé, když.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Objekt ukládání do mezipaměti příklad 2  
 V tomto příkladu Pokud spuštění různých dotazů, které vracejí na stejném řádku z databáze, zobrazí se odkaz na stejný objekt v paměti pokaždé, když.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
