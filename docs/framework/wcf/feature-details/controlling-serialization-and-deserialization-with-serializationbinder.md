---
title: "Řízení serializace a deserializace pomocí třídy SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="c0d73-102">Řízení serializace a deserializace pomocí třídy SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="c0d73-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="c0d73-103">Během serializace formátování přenáší informace požadované pro vytvoření instance objektu správný typ a verze.</span><span class="sxs-lookup"><span data-stu-id="c0d73-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="c0d73-104">Tyto informace zahrnují obecně zadejte úplný název a název sestavení objektu.</span><span class="sxs-lookup"><span data-stu-id="c0d73-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="c0d73-105">Ve výchozím nastavení používá deserializace tyto informace k vytvoření instance objektu stejné.</span><span class="sxs-lookup"><span data-stu-id="c0d73-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="c0d73-106">Někteří uživatelé mohou potřebovat k řízení které třídy k serializaci a deserializaci, buď protože původní třída nemusí existovat v počítači provádění deserializace, původní třída přesunul mezi sestavení nebo jinou verzi třídy je vyžadován na Server a klienta.</span><span class="sxs-lookup"><span data-stu-id="c0d73-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c0d73-107">[Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span><span class="sxs-lookup"><span data-stu-id="c0d73-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c0d73-108">Tato funkce je dostupná pouze při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c0d73-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="c0d73-109">Pomocí třídy SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="c0d73-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="c0d73-110"><xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="c0d73-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="c0d73-111">Pokud chcete řídit typy používané během serializace a deserializace, odvození třídy z <xref:System.Runtime.Serialization.SerializationBinder> a přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & autoUpgrade = True a <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)? qualifyHint = False & autoUpgrade = True metody.</span><span class="sxs-lookup"><span data-stu-id="c0d73-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True methods.</span></span> <span data-ttu-id="c0d73-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & autoUpgrade = True metoda trvá <xref:System.Type> a vrátí název sestavení a typu.</span><span class="sxs-lookup"><span data-stu-id="c0d73-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="c0d73-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = True metoda trvá sestavení a název typu a vrátí <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c0d73-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d73-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0d73-114">See Also</span></span>  
 [<span data-ttu-id="c0d73-115">Serializace a deserializace</span><span class="sxs-lookup"><span data-stu-id="c0d73-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="c0d73-116">Použití vazače serializace</span><span class="sxs-lookup"><span data-stu-id="c0d73-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
