---
title: Typy izolace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
ms.openlocfilehash: d85625b99603c0bd81346cf2076b8efe0e1bba42
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523885"
---
# <a name="types-of-isolation"></a>Typy izolace
Přístup k izolovanému úložišti je vždy omezen na uživatele, který jej vytvořil. K implementaci tohoto typu izolace používá soubor RUNTIME společného jazyka stejnou představu o identitě uživatele, kterou rozpozná operační systém, což je identita přidružená k procesu, ve kterém je kód spuštěn při otevření úložiště. Tato identita je ověřená identita uživatele, ale zosobnění může způsobit dynamickou změnu identity aktuálního uživatele.  
  
 Přístup k izolovanému úložišti je také omezen podle identity přidružené k doméně a sestavení aplikace nebo k samotnému sestavení. Runtime získá tyto identity následujícími způsoby:  
  
- Identita domény představuje důkaz aplikace, která v případě webové aplikace může být úplná adresa URL. U kódu hostovaného prostředím může být identita domény založena na cestě k adresáři aplikace. Pokud například spustitelný soubor běží z cesty C:\Office\MyApp.exe, bude identita domény C:\Office\MyApp.exe.  
  
- Identita sestavení je důkazem sestavení. To může pocházet z kryptografického digitálního podpisu, což může být [silný název](../assembly/strong-named.md)sestavení , vydavatel softwaru sestavení nebo jeho identita url. Pokud má sestavení silný název i identitu vydavatele softwaru, použije se identita vydavatele softwaru. Pokud sestavení pochází z Internetu a je nepodepsané, identita adresy URL se používá. Další informace o sestaveních a silných názvech naleznete v [tématu Programování pomocí sestavení](/dotnet/standard/assembly/index).  
  
- Roamingová úložiště se přesouvají s uživatelem, který má cestovní profil uživatele. Soubory jsou zapsány do síťového adresáře a stahovány do libovolného počítače, ke které se uživatel přihlásí. Další informace o cestovních <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>uživatelských profilech naleznete v tématu .  
  
 Kombinací konceptů identity uživatele, domény a sestavení může izolované úložiště izolovat data následujícími způsoby, z nichž každý má své vlastní scénáře použití:  
  
- [Izolace podle uživatele a sestavení](#UserAssembly)  
  
- [Izolace podle uživatele, domény a sestavení](#UserDomainAssembly)  
  
 Některou z těchto izolací lze kombinovat s cestovním uživatelským profilem. Další informace naleznete v části [Izolované úložiště a roaming](#Roaming).  
  
 Následující obrázek znázorňuje, jak jsou obchody izolovány v různých oborech:  
  
 ![Diagram, který zobrazuje izolaci podle uživatele a sestavení.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Všimněte si, že s výjimkou roamingových úložišť je izolované úložiště vždy implicitně izolováno počítačem, protože používá úložiště, která jsou pro daný počítač místní.  
  
> [!IMPORTANT]
> Izolované úložiště není dostupné pro aplikace pro Windows 8.x Store. Místo toho použijte třídy `Windows.Storage` dat aplikace v oborech názvů zahrnutých v rozhraní API prostředí Windows Runtime k ukládání místních dat a souborů. Další informace naleznete v [tématu Data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) v Centru pro vývoj systému Windows.  
  
<a name="UserAssembly"></a>
## <a name="isolation-by-user-and-assembly"></a>Izolace podle uživatele a sestavení  
 Pokud sestavení, které používá úložiště dat musí být přístupné z domény libovolné aplikace, izolace podle uživatele a sestavení je vhodné. V této situaci se obvykle používá izolované úložiště k ukládání dat, která platí ve více aplikacích a není vázána na žádnou konkrétní aplikaci, jako je například jméno uživatele nebo informace o licenci. Pro přístup k úložišti izolovanému uživatelem a sestavením musí být kód důvěryhodný pro přenos informací mezi aplikacemi. Izolace podle uživatele a sestavení je obvykle povolena v intranetu, ale ne v Síti Internet. Volání statické <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> metody a předávání v <xref:System.IO.IsolatedStorage.IsolatedStorageScope> uživatele a sestavení vrátí úložiště s tímto druhem izolace.  
  
 Následující příklad kódu načte úložiště, které je izolováno uživatelem a sestavením. Úložiště lze přistupovat prostřednictvím objektu. `isoFile`  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Příklad, který používá parametry evidence, naleznete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tuto zkratku nelze použít k otevření obchodů, které jsou schopné roamingu; v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> takových případech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>
## <a name="isolation-by-user-domain-and-assembly"></a>Izolace podle uživatele, domény a sestavení  
 Pokud vaše aplikace používá sestavení jiného výrobce, které vyžaduje úložiště soukromých dat, můžete použít izolované úložiště k ukládání soukromých dat. Izolace podle uživatele, domény a sestavení zajišťuje, že pouze kód v daném sestavení přístup k datům a pouze v případě, že sestavení je používán o aplikaci, která byla spuštěna při sestavení vytvořil úložiště a pouze v případě, že uživatel, pro kterého byl vytvořen úložiště spustí aplikaci. Izolace podle uživatele, domény a sestavení udržuje sestavení jiného výrobce z úniku dat do jiných aplikací. Tento typ izolace by měla být výchozí volbou, pokud víte, že chcete použít izolované úložiště, ale nejste si jisti, jaký typ izolace použít. Volání statické <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile> a předávání v uživateli, <xref:System.IO.IsolatedStorage.IsolatedStorageScope> doméně a sestavení vrátí úložiště s tímto druhem izolace.  
  
 Následující příklad kódu načte úložiště izolované uživatelem, doménou a sestavením. Úložiště lze přistupovat prostřednictvím objektu. `isoFile`  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Jiná metoda je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tuto zkratku nelze použít k otevření obchodů, které jsou schopné roamingu; v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> takových případech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>
## <a name="isolated-storage-and-roaming"></a>Izolované úložiště a roaming  
 Cestovní profily uživatelů jsou funkce systému Windows, která umožňuje uživateli nastavit identitu v síti a použít tuto identitu k přihlášení do libovolného síťového počítače a přenášet všechna přizpůsobená nastavení. Sestavení, které používá izolované úložiště, může určit, že izolované úložiště uživatele by se mělo přesunout s cestovním profilem uživatele. Roaming lze použít ve spojení s izolací uživatelem a sestavením nebo s izolací podle uživatele, domény a sestavení. Pokud se nepoužívá obor roamingu, obchody nebudou přetékat ani v případě, že je použit cestovní profil uživatele.  
  
 Následující příklad kódu načte úložiště roamingu izolované uživatelem a sestavením. Úložiště lze přistupovat prostřednictvím objektu. `isoFile`  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Obor domény lze přidat k vytvoření cestovního úložiště izolovaného uživatelem, doménou a aplikací. Následující příklad kódu ukazuje toto.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
