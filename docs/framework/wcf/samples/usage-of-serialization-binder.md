---
title: Použití vazače serializace
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138645"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="0d261-102">Použití vazače serializace</span><span class="sxs-lookup"><span data-stu-id="0d261-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="0d261-103">Tento příklad ukazuje, jak použít <xref:System.Runtime.Serialization.SerializationBinder> ke změně verze obecného typu při jeho serializaci.</span><span class="sxs-lookup"><span data-stu-id="0d261-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0d261-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="0d261-104">Demonstrates</span></span>  
 <span data-ttu-id="0d261-105"><xref:System.Runtime.Serialization.SerializationBinder><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="0d261-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0d261-106">Účely</span><span class="sxs-lookup"><span data-stu-id="0d261-106">Discussion</span></span>  
 <span data-ttu-id="0d261-107">Tento příklad ukazuje, jak mohou dvě entity, které cílí na různé verze .NET Framework, komunikovat pomocí binárního formátovacího modulu a pořadače serializace.</span><span class="sxs-lookup"><span data-stu-id="0d261-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="0d261-108">Tato ukázka byla vyvinuta pomocí vzdálené komunikace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="0d261-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="0d261-109">Skládá se ze serveru, který je cílen .NET Framework 4, který implementuje kontrakt s obecnými typy a dvěma různými klienty, jeden cílí .NET Framework 2,0 a jiný cílí .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0d261-109">It consists of a server targeting .NET Framework 4, which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting .NET Framework 4.</span></span>  
  
 <span data-ttu-id="0d261-110">Server připojí <xref:System.Runtime.Serialization.SerializationBinder> k binárnímu formátovacímu modulu, aby bylo možné změnit verzi typů odpovídající serializaci, aby oba klienti mohli tyto typy rekonstruovat správně.</span><span class="sxs-lookup"><span data-stu-id="0d261-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d261-111">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="0d261-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="0d261-112">Chcete-li spustit klienta, klikněte pravým tlačítkem myši na řešení, SBGenericsVTS (6 projektů) a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0d261-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="0d261-113">V možnosti **společné vlastnosti**vyberte možnost **projekt po spuštění**a pak vyberte **více projektů po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="0d261-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="0d261-114">Nejprve vyberte **Server** a pak **Client20** a pak **Client40**.</span><span class="sxs-lookup"><span data-stu-id="0d261-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="0d261-115">Vyberte akci **Spustit** pro tyto tři projekty a nechejte nastavenou možnost **žádná**.</span><span class="sxs-lookup"><span data-stu-id="0d261-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="0d261-116">Klikněte na **OK** a potom stisknutím klávesy F5 spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="0d261-116">Click **OK** and then press F5 to run the sample.</span></span>
