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
ms.openlocfilehash: 49708175f8501c735a77b0f7f965a106b6e086f2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45652989"
---
# <a name="types-of-isolation"></a>Typy izolace
Přístup k izolovanému úložišti je vždy omezen na uživatele, který jej vytvořil. K implementaci tohoto typu izolace, modul common language runtime používá stejný pojem identitu uživatele, který rozpoznává operační systém, který je identitu přidruženou k procesu, ve kterém kód běží při otevření úložiště. Tato identita je identity ověřeného uživatele, ale zosobnění může způsobit identity aktuálního uživatele, aby dynamicky měnit.  
  
 Přístup k izolované úložiště je také omezen podle identita spojená s doménou vaší aplikace a sestavení, nebo pouze k sestavení. Modul runtime získá tyto identity následujícími způsoby:  
  
-   Identitu domény představuje doklad o aplikaci, které se v případě webové aplikace může být úplnou adresu URL. Pro prostředí hostovaná kód identitu domény může zakládat na cestu k adresáři aplikace. Pokud spuštění spustitelného souboru z cesty C:\Office\MyApp.exe identitu domény by třeba C:\Office\MyApp.exe.  
  
-   Identita sestavení je legitimaci sestavení. To může pocházet z kryptografických digitální podpis, který může být sestavení [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), sestavení nebo jeho adresa URL identity vydavatele softwaru. Pokud sestavení se silným názvem a identita vydavatele softwaru, použije se identita vydavatele softwaru. Pokud sestavení pocházejí z Internetu a bez znaménka, použije se adresa URL identity. Další informace o sestavení a silných názvů najdete v tématu [programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Roamingové úložiště přesunout jako uživatel, který má cestovní profil uživatele. Soubory jsou zapsány do síťovému adresáři a se stáhnou na libovolném počítači se uživatel přihlásí. Další informace o cestovní profily uživatelů najdete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Díky kombinaci koncepty uživatele, domény a identitu sestavení, lze izolovat izolované úložiště dat následujícími způsoby, z nichž každá má svou vlastní scénáře použití:  
  
-   [Izolace podle uživatele a sestavení](#UserAssembly)  
  
-   [Izolace podle uživatele, domény a sestavení](#UserDomainAssembly)  
  
 Obě tyto izolace zkombinovat s cestovní profil uživatele. Další informace najdete v části [izolované úložiště a Roaming](#Roaming).  
  
 Následující obrázek ukazuje, jak jsou izolované úložiště v různých rozsazích.  
  
 ![Izolace podle uživatele a sestavení](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Typy izolovaného úložiště  
  
 Všimněte si, že kromě cestovních úložišť, izolované úložiště je vždy implicitně izolována počítačem vzhledem k tomu používá zařízení úložiště, které jsou místní pro daný počítač.  
  
> [!IMPORTANT]
>  Izolované úložiště není k dispozici pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Místo toho použít třídy aplikačních dat v `Windows.Storage` obory názvů součástí [!INCLUDE[wrt](../../../includes/wrt-md.md)] rozhraní API pro ukládání místních dat a souborů. Další informace najdete v tématu [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) Windows Dev Center.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Izolace podle uživatele a sestavení  
 Při sestavení, která používá data ukládat musí být přístupná z libovolné aplikace domény, je vhodné izolace podle uživatele a sestavení. V takovém případě obvykle izolovaného úložiště se používá k ukládání dat, které platí mezi více aplikacemi a se neváže k určité aplikaci, jako je například uživatelské jméno nebo informace o licencích. Kód pro přístup k úložišti izolováno podle uživatele a sestavení, musí být důvěryhodný k přenosu informací mezi aplikacemi. Izolace podle uživatele a sestavení je obvykle povolen v sítích intranet, ale ne na Internetu. Volání statické <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> metoda a předáním uživatele a sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageScope> vrátí úložiště tento typ izolace.  
  
 Následující příklad kódu načte úložiště, které je izolováno podle uživatele a sestavení. Úložiště lze přistupovat prostřednictvím `isoFile` objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Příklad, který používá parametry důkazy, naleznete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Metoda je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tento zástupce nelze použít k otevření úložiště, které podporují roamingu. použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> v takových případech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Izolace podle uživatele, domény a sestavení  
 Pokud vaše aplikace používá sestavení třetích stran, které vyžaduje soukromé úložiště dat, můžete k ukládání dat soukromých izolovaného úložiště. Izolace podle uživatele, domény a sestavení zajistí, že pouze kód v daném sestavení můžete přistupovat k datům a pouze v případě sestavení používá aplikaci, která byla spuštěna, když sestavení vytvořil úložiště, a pouze v případě, že uživatel, pro kterého byla vytvořena ve storu spustí  aplikace. Izolace podle uživatele, domény a sestavení udržuje sestavení třetích stran, abyste zabránili úniku dat do jiných aplikací. Tento typ izolace by měl být výchozí volba, pokud víte, že chcete používat izolované úložiště, ale nejste jisti, jaký typ izolace použít. Volání statické <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile> a předávání uživatele, domény a sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageScope> vrátí úložiště tento typ izolace.  
  
 Následující příklad kódu načte úložiště izolováno podle uživatele, domény a sestavení. Úložiště lze přistupovat prostřednictvím `isoFile` objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Jinou metodou je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tento zástupce nelze použít k otevření úložiště, které podporují roamingu. použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> v takových případech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Izolované úložiště a roamingu  
 Cestovní profily uživatelů jsou funkcí Windows, která umožňuje uživateli nastavit identitu v síti a použít tuto identitu pro přihlášení na všechny počítače v síti, může přenos přes všechny individuální nastavení. Sestavení, které používá izolované úložiště můžete určit, že uživatele izolovaného úložiště by měl přejít bez cestovní profil uživatele. Roamingu můžete použít ve spojení s izolace podle uživatele a sestavení nebo izolace podle uživatele, domény a sestavení. Pokud není použit obor roamingu, úložišť nepřenesou i v případě, že se používá cestovní profil uživatele.  
  
 Následující příklad kódu načte roamingové úložiště izolováno podle uživatele a sestavení. Úložiště lze přistupovat prostřednictvím `isoFile` objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Obor domény je přidat k vytvoření roamingové úložiště izolováno podle uživatele, domény a aplikace. Následující příklad kódu ukazuje to.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
