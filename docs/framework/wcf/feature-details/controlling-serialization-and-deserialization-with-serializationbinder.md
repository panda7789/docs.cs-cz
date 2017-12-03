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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67afc6dbc069678c8fb692f70bc0e7a0a12b1076
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="29b6b-102">Řízení serializace a deserializace pomocí třídy SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="29b6b-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="29b6b-103">Během serializace formátování přenáší informace požadované pro vytvoření instance objektu správný typ a verze.</span><span class="sxs-lookup"><span data-stu-id="29b6b-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="29b6b-104">Tyto informace zahrnují obecně zadejte úplný název a název sestavení objektu.</span><span class="sxs-lookup"><span data-stu-id="29b6b-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="29b6b-105">Ve výchozím nastavení používá deserializace tyto informace k vytvoření instance objektu stejné.</span><span class="sxs-lookup"><span data-stu-id="29b6b-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="29b6b-106">Někteří uživatelé mohou potřebovat k řízení které třídy k serializaci a deserializaci, buď protože původní třída nemusí existovat v počítači provádění deserializace, původní třída přesunul mezi sestavení nebo jinou verzi třídy je vyžadován na Server a klienta.</span><span class="sxs-lookup"><span data-stu-id="29b6b-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="29b6b-107">[Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span><span class="sxs-lookup"><span data-stu-id="29b6b-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="29b6b-108">Tato funkce je dostupná pouze při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="29b6b-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="29b6b-109">Pomocí třídy SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="29b6b-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="29b6b-110"><xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="29b6b-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="29b6b-111">Pokud chcete řídit typy používané během serializace a deserializace, odvození třídy z <xref:System.Runtime.Serialization.SerializationBinder> a přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody.</span><span class="sxs-lookup"><span data-stu-id="29b6b-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> methods.</span></span> <span data-ttu-id="29b6b-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metoda trvá <xref:System.Type> a vrátí název sestavení a typu.</span><span class="sxs-lookup"><span data-stu-id="29b6b-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="29b6b-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda přebírá název sestavení a typ a vrátí <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="29b6b-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b6b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="29b6b-114">See Also</span></span>  
 [<span data-ttu-id="29b6b-115">Serializace a deserializace</span><span class="sxs-lookup"><span data-stu-id="29b6b-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="29b6b-116">Použití vazače serializace</span><span class="sxs-lookup"><span data-stu-id="29b6b-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
