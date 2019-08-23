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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8875ed10c4cb144995b602287f904d3c98dcdb39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948768"
---
# <a name="types-of-isolation"></a>Typy izolace
Přístup k izolovanému úložišti je vždycky omezený na uživatele, který ho vytvořil. Pro implementaci tohoto typu izolace používá modul CLR stejný pojem identity uživatele, jakou operační systém rozpozná, což je identita přidružená k procesu, ve kterém kód běží při otevření úložiště. Tato identita je identita ověřeného uživatele, ale zosobnění může způsobit, že se identita aktuálního uživatele dynamicky mění.  
  
 Přístup k izolovanému úložišti je také omezen na základě identity přidružené k doméně a sestavení aplikace nebo samotném sestavení. Modul runtime získá tyto identity následujícími způsoby:  
  
- Doménová identita představuje legitimaci aplikace, která v případě webové aplikace může být úplnou adresou URL. V případě kódu hostovaného v prostředí může být identita domény založená na cestě k adresáři aplikace. Například pokud se spustitelný soubor spouští z cesty C:\Office\MyApp.exe, bude identita domény C:\Office\MyApp.exe.  
  
- Identita sestavení je důkazem sestavení. Může to pocházet z kryptografického digitálního podpisu, který může být silným [názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)sestavení, vydavatelem sestavení nebo jeho identitou URL. Pokud má sestavení silný název a identitu vydavatele softwaru, použije se identita vydavatele softwaru. Pokud sestavení pochází z Internetu a není podepsané, je použita identita URL. Další informace o sestaveních a silných názvech naleznete v tématu [programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
- Roamingové úložiště se přesouvá s uživatelem, který má cestovní profil uživatele. Soubory jsou zapsány do síťového adresáře a jsou staženy do libovolného počítače, do kterého se uživatel přihlašuje. Další informace o cestovních profilech uživatelů najdete <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>v tématu.  
  
 Díky kombinování konceptů identit uživatelů, domén a sestavení může izolované úložiště izolovat data následujícími způsoby, z nichž každá má vlastní scénáře použití:  
  
- [Izolace podle uživatele a sestavení](#UserAssembly)  
  
- [Izolace podle uživatele, domény a sestavení](#UserDomainAssembly)  
  
 Jednu z těchto izolací můžete kombinovat s uživatelským profilem roamingu. Další informace najdete v části [izolované úložiště a roaming](#Roaming).  
  
 Následující obrázek ukazuje, jak jsou obchody izolované v různých oborech:  
  
 ![Diagram, který zobrazuje izolaci podle uživatele a sestavení.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 Všimněte si, že s výjimkou úložišť roamingu je izolované úložiště vždycky implicitně izolované počítačem, protože používá úložná zařízení, která jsou místní pro daný počítač.  
  
> [!IMPORTANT]
> Izolované úložiště není pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace k dispozici. Místo toho použijte aplikační datové třídy v `Windows.Storage` oborech názvů obsažených v rozhraní prostředí Windows Runtime API k ukládání místních dat a souborů. Další informace najdete v tématu [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) na stránce Windows Dev Center.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Izolace podle uživatele a sestavení  
 Pokud je nutné sestavení, které používá úložiště dat, přístupné z jakékoli domény aplikace, je vhodná izolace podle uživatele a sestavení. V takové situaci se obvykle používá izolované úložiště k ukládání dat, která se vztahují na více aplikací, a není vázána na žádnou konkrétní aplikaci, například na jméno uživatele nebo informace o licenci. Aby bylo možné získat přístup k úložišti izolovanému podle uživatele a sestavení, musí být kód důvěryhodný k přenosu informací mezi aplikacemi. Typicky se izolace podle uživatele a sestavení povoluje v intranetech, ale ne na internetu. Volání statické <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> metody a předání v rámci uživatele a sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageScope> vrátí úložiště s tímto druhem izolace.  
  
 Následující příklad kódu načte úložiště izolované uživatelem a sestavením. K úložišti je možné přistupovat `isoFile` prostřednictvím objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Příklad, který používá parametry legitimace, naleznete v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>tématu.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Metoda je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tuto klávesovou zkratku nejde použít k otevření úložišť, která jsou schopná roamingu. v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> takových případech použijte.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Izolace podle uživatele, domény a sestavení  
 Pokud vaše aplikace používá sestavení třetí strany, které vyžaduje privátní úložiště dat, můžete k uložení privátních dat použít izolované úložiště. Izolace podle uživatele, domény a sestavení zajišťuje, aby k datům měl přístup pouze kód v daném sestavení, a pouze v případě, že je sestavení používáno aplikací, která byla spuštěna v době, kdy sestavení vytvořilo úložiště, a pouze v případě, že uživatel, pro kterého byl obchod vytvořen, spouští  použití. Izolace podle uživatele, domény a sestavení udržuje sestavení třetí strany proti úniku dat do jiných aplikací. Tento typ izolace by měl být výchozí volbou, pokud víte, že chcete použít izolované úložiště, ale nevíte, jaký typ izolace použít. Volání statické <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile> metody a předání v rámci uživatele, domény a sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageScope> vrátí úložiště s tímto druhem izolace.  
  
 Následující příklad kódu načte úložiště izolované uživatelem, doménou a sestavením. K úložišti je možné přistupovat `isoFile` prostřednictvím objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Další metoda je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tuto klávesovou zkratku nejde použít k otevření úložišť, která jsou schopná roamingu. v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> takových případech použijte.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Izolované úložiště a roaming  
 Cestovní profily uživatelů jsou funkce systému Windows, která umožňuje uživateli nastavit identitu v síti a pomocí této identity se přihlašovat k jakémukoli síťovému počítači a přitom přenášet všechna individuální nastavení. Sestavení, které používá izolované úložiště, může určit, že izolované úložiště uživatele by se mělo přesunout pomocí cestovního profilu uživatele. Roaming lze použít ve spojení s izolací podle uživatele a sestavení nebo s izolací podle uživatele, domény a sestavení. Pokud se obor roamingu nepoužívá, úložiště se neroaminge ani v případě, že se použije cestovní profil uživatele.  
  
 Následující příklad kódu načte cestovní úložiště izolované uživatelem a sestavením. K úložišti je možné přistupovat `isoFile` prostřednictvím objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Obor domény lze přidat k vytvoření cestovního úložiště, které je izolované uživatelem, doménou a aplikací. Následující příklad kódu to demonstruje.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
