---
title: Identita objektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: dff5642b2490cd3935dba3b3d04cd62082249c32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915715"
---
# <a name="object-identity"></a>Identita objektu
Objekty v modulu runtime mají jedinečné identity. Dvě proměnné, které odkazují na stejný objekt, ve skutečnosti odkazují na stejnou instanci objektu. Vzhledem k tomu, že se změny provedené pomocí cesty přes jednu proměnnou projeví okamžitě po druhém.  
  
 Řádky v tabulce relační databáze nemají jedinečné identity. Vzhledem k tomu, že každý řádek má jedinečný primární klíč, žádné dva řádky nesdílejí stejnou hodnotu klíče. Tento fakt však omezuje pouze obsah databázové tabulky.  
  
 Ve skutečnosti se data nejčastěji přibývají z databáze a do jiné úrovně, kde aplikace spolupracuje. Toto je model, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje. Když se data z databáze nastanou jako řádky, neočekává se, že dva řádky, které reprezentují stejná data, ve skutečnosti odpovídají stejným instancím řádků. Pokud se dotaz na konkrétního zákazníka zobrazí dvakrát, získáte dva řádky dat. Každý řádek obsahuje stejné informace.  
  
 U objektů, které očekáváte něco jiného. Očekáváte, že pokud budete chtít <xref:System.Data.Linq.DataContext> , aby se tytéž informace opakovaně vyžádaly, zobrazí se ve skutečnosti stejná instance objektu. Toto chování očekáváte, protože objekty mají zvláštní význam pro vaši aplikaci a očekáváte, že se budou chovat jako objekty. Navrhli jste je jako hierarchie nebo grafy. Očekáváte, že byste je načetli jako takové, a nedostanete tak velké množství replikovaných instancí, protože jste se o stejný úkol vyžádali více než jednou.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástrojispravujeidentituobjektu <xref:System.Data.Linq.DataContext> . Pokaždé, když načtete nový řádek z databáze, zapíše se řádek do tabulky identity podle jeho primárního klíče a vytvoří se nový objekt. Pokaždé, když načtete stejný řádek, původní instance objektu se vrátí zpět do aplikace. Tímto způsobem se <xref:System.Data.Linq.DataContext> přeloží koncept identity, jak je vidět databáze (tj. primární klíče), do konceptu identity, ke které se jazyk (tj. instance) zobrazuje. Aplikace uvidí pouze objekt ve stavu, ve kterém byl poprvé načten. Nová data, pokud jsou odlišná, se zahodí. Další informace najdete v tématu [načítání objektů z mezipaměti identit](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Tento přístup používá ke správě integrity místních objektů za účelem podpory optimistické aktualizace. Vzhledem k tomu, že jedinými změnami, ke kterým dochází po prvním vytvoření objektu, jsou ty, které udělala aplikace, záměr aplikace je jasný. Pokud došlo ke změnám, které dostanou externí strana, jsou identifikovány v době `SubmitChanges()` volání.  
  
> [!NOTE]
> Pokud je objekt požadovaný dotazem snadno identifikovatelný jako ten, který je už načtený, neprovede se žádný dotaz. Tabulka identity funguje jako mezipaměť všech dříve načtených objektů.  
  
## <a name="examples"></a>Příklady  
  
### <a name="object-caching-example-1"></a>Příklad ukládání objektů do mezipaměti – příklad 1  
 Pokud v tomto příkladu spustíte stejný dotaz dvakrát, obdržíte vždy odkaz na stejný objekt v paměti.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Příklad ukládání objektů do mezipaměti – příklad 2  
 Pokud v tomto příkladu spustíte jiné dotazy, které vracejí stejný řádek z databáze, obdržíte vždy odkaz na stejný objekt v paměti.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
