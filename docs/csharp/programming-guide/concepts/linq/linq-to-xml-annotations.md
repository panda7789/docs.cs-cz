---
title: Linq na poznámky XML3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66689941"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="291de-102">Poznámky v LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="291de-102">LINQ to XML Annotations</span></span>

<span data-ttu-id="291de-103">Poznámky v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aplikaci umožňují přidružit libovolný objekt libovolného typu k libovolné součásti XML ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="291de-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="291de-104">Chcete-li přidat poznámku k součásti <xref:System.Xml.Linq.XElement> XML, například nebo <xref:System.Xml.Linq.XAttribute>, zavolejte metodu. <xref:System.Xml.Linq.XObject.AddAnnotation%2A></span><span class="sxs-lookup"><span data-stu-id="291de-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="291de-105">Poznámky načíst podle typu.</span><span class="sxs-lookup"><span data-stu-id="291de-105">You retrieve annotations by type.</span></span>

<span data-ttu-id="291de-106">Všimněte si, že poznámky nejsou součástí informační sady XML; nejsou serializovány nebo deserializovány.</span><span class="sxs-lookup"><span data-stu-id="291de-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="291de-107">Metody</span><span class="sxs-lookup"><span data-stu-id="291de-107">Methods</span></span>

<span data-ttu-id="291de-108">Při práci s poznámkami můžete použít následující metody:</span><span class="sxs-lookup"><span data-stu-id="291de-108">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="291de-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="291de-109">Method</span></span>|<span data-ttu-id="291de-110">Popis</span><span class="sxs-lookup"><span data-stu-id="291de-110">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="291de-111">Přidá objekt do seznamu poznámk <xref:System.Xml.Linq.XObject>y .</span><span class="sxs-lookup"><span data-stu-id="291de-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="291de-112">Získá první objekt poznámky zadaného typu <xref:System.Xml.Linq.XObject>z .</span><span class="sxs-lookup"><span data-stu-id="291de-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="291de-113">Získá kolekci poznámky zadaného typu pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="291de-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="291de-114">Odebere poznámky zadaného typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="291de-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
