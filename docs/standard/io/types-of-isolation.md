---
title: Typy izolace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a7e9b28601970aecd139d2027bc0ebc73e869fc
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2018
---
# <a name="types-of-isolation"></a>Typy izolace
Přístup k izolovanému úložišti je vždy omezen na uživatele, který ho vytvořil. Implementaci tohoto typu izolace, modul common language runtime používá stejný pojem identitu uživatele, který rozpoznává operační systém, což je identita spojená s procesu, ve kterém kód běží, když je otevřen úložišti. Tato identita je ověřená identita uživatele, ale zosobnění může způsobit, že identita aktuálního uživatele, aby se dynamicky mění.  
  
 Přístup k izolovanému úložišti je také omezen podle identita spojená s doménou a sestavení aplikace, nebo pouze k sestavení. Modul runtime získává tyto identity následujícími způsoby:  
  
-   Identita domény představuje doklad o aplikaci, kterou u webové aplikace může být úplnou adresu URL. Pro hostované prostředí kód identita domény může být založen na cestě k adresáři aplikace. Pokud spustitelný soubor spouští z cesty C:\Office\MyApp.exe, identita domény by třeba C:\Office\MyApp.exe.  
  
-   Identita sestavení je důkaz sestavení. Ta může pocházet z kryptografického digitálního podpisu, který může být toto sestavení [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), vydavatele softwaru sestavení nebo totožnost adresy URL. Sestavení se silným názvem i identitu vydavatele softwaru, se používá identity vydavatele softwaru. Pokud sestavení pochází z Internetu a není podepsaný, použije se adresa URL identity. Další informace o sestavení a silné názvy najdete v tématu [programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Přenosná úložiště se přesouvají s uživatelem, který má cestovní profil uživatele. Soubory jsou zapsány k síťovému adresáři a se stáhnou do libovolného počítače se uživatel přihlásí do. Další informace o cestovní profily uživatelů najdete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 Kombinací koncepty uživatele, domény a sestavení identity lze izolovat izolované úložiště dat následujícími způsoby, z nichž každá má svou vlastní scénáře použití:  
  
-   [Izolace uživatelů a sestavení](#UserAssembly)  
  
-   [Izolace uživatele, domény a sestavení](#UserDomainAssembly)  
  
 Obě tyto izolace mohou být kombinovány s cestovní profil uživatele. Další informace najdete v části [izolované úložiště a Roaming](#Roaming).  
  
 Následující obrázek ukazuje, jak jsou izolované úložiště v různých oborech.  
  
 ![Izolace uživatelů a sestavení](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Typy izolovaného úložiště  
  
 Všimněte si, že s výjimkou přenosných úložišť, izolované úložiště je vždy implicitně izolované počítačem protože používá zařízení úložiště, které jsou místní pro daný počítač.  
  
> [!IMPORTANT]
>  Izolované úložiště není k dispozici pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Místo toho použít třídy data aplikací v `Windows.Storage` obory názvů, které jsou součástí [!INCLUDE[wrt](../../../includes/wrt-md.md)] rozhraní API pro uložení místního data a soubory. Další informace najdete v tématu [data aplikací](/previous-versions/windows/apps/hh464917(v=win.10)) ve službě Windows Dev Center.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Izolace uživatelů a sestavení  
 Při sestavení, které používá data uložit, musí být přístupný z domény jakékoli aplikace, je vhodné izolace uživatelů a sestavení. V této situaci obvykle izolované úložiště se používá k ukládání dat, které platí napříč různými aplikacemi a není vázána k určité aplikaci, například uživatelské jméno nebo informace o licencích. Kód pro přístup k úložišti izolované uživatelem a sestavení, musí být důvěryhodný k přenosu informací mezi aplikacemi. Izolace uživatelů a sestavení je obvykle povolena na intranetu, ale není na Internetu. Volání metody statických <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> metoda a předávání uživatele a sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageScope> vrátí úložiště s tímto typem izolace.  
  
 Následující příklad kódu načte úložiště, která je izolovaná podle uživatele a sestavení. Windows store je přístupná prostřednictvím `isoFile` objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Příklad, který používá parametry důkaz, naleznete v části <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Metoda je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tento zástupce nelze použít k otevření úložiště, které podporují roamingu. použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> v takových případech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Izolace uživatele, domény a sestavení  
 Pokud vaše aplikace používá sestavení třetích stran, které vyžaduje soukromé úložiště dat, můžete k uložení dat o privátní izolovaného úložiště. Izolace uživatele, domény a sestavení zajistí, že pouze kód v daném sestavení měli přístup k datům a jenom v případě, že používá sestavení aplikace, který byl spuštěn, když sestavení vytvořil úložiště, a jenom v případě, že uživatel, pro kterého byla vytvořena úložiště spustí  aplikace. Izolace uživatele, domény a sestavení udržuje sestavení třetích stran, abyste zabránili úniku dat do jiných aplikací. Tento typ izolace by měl být výchozí volbou, pokud víte, že chcete používat izolované úložiště, ale nejste jisti, jaký typ izolace použít. Volání metody statických <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> a předávání v uživatele, domény a sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageScope> vrátí úložiště s tímto typem izolace.  
  
 Následující příklad kódu načte úložiště izolované uživatele, domény a sestavení. Windows store je přístupná prostřednictvím `isoFile` objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Další možností je k dispozici jako zástupce, jak je znázorněno v následujícím příkladu kódu. Tento zástupce nelze použít k otevření úložiště, které podporují roamingu. použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> v takových případech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Izolované úložiště a Roaming  
 Cestovní profily uživatelů jsou funkce systému Windows, která umožňuje uživatelům nastavit identity v síti a použít tuto identitu pro přihlášení na všechny počítače v síti, provedení přes všechny individuální nastavení. Sestavení, které používá izolované úložiště můžete zadat, že izolovaného úložiště uživatele přesuňte s cestovní profil uživatele. Roaming můžete použít ve spojení s izolací uživatelů a sestavení nebo s izolací podle uživatele, domény a sestavení. Pokud se nepoužívá obor roamingu, úložiště nebudou cestovat i v případě, že se používá cestovní profil uživatele.  
  
 Následující příklad kódu načte cestovní úložiště izolované podle uživatele a sestavení. Windows store je přístupná prostřednictvím `isoFile` objektu.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Obor domény mohou být přidány pro vytvoření roamingu úložiště izolované uživatelem, domény a aplikace. Následující příklad kódu ukazuje to.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
