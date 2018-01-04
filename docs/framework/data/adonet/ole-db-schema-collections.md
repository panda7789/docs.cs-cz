---
title: "Kolekcemi schémat OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="a8eee-102">Kolekcemi schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="a8eee-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="a8eee-103">Tato část popisuje podporu kolekci schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="a8eee-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="a8eee-104">Zprostředkovatel Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="a8eee-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="a8eee-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="a8eee-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="a8eee-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="a8eee-106">Tables</span></span>  
  
-   <span data-ttu-id="a8eee-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="a8eee-107">Columns</span></span>  
  
-   <span data-ttu-id="a8eee-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8eee-108">Procedures</span></span>  
  
-   <span data-ttu-id="a8eee-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a8eee-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="a8eee-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="a8eee-110">Catalog</span></span>  
  
-   <span data-ttu-id="a8eee-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="a8eee-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="a8eee-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="a8eee-112">Tables</span></span>  
  
|<span data-ttu-id="a8eee-113">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-113">ColumnName</span></span>|<span data-ttu-id="a8eee-114">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-115">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-116">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-116">String</span></span>|  
|<span data-ttu-id="a8eee-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-118">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-118">String</span></span>|  
|<span data-ttu-id="a8eee-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-119">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-120">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-120">String</span></span>|  
|<span data-ttu-id="a8eee-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-121">TABLE_TYPE</span></span>|<span data-ttu-id="a8eee-122">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-122">String</span></span>|  
|<span data-ttu-id="a8eee-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-123">TABLE_GUID</span></span>|<span data-ttu-id="a8eee-124">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-124">Guid</span></span>|  
|<span data-ttu-id="a8eee-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-125">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-126">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-126">String</span></span>|  
|<span data-ttu-id="a8eee-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-127">TABLE_PROPID</span></span>|<span data-ttu-id="a8eee-128">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-128">Int64</span></span>|  
|<span data-ttu-id="a8eee-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-129">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-130">DateTime</span></span>|  
|<span data-ttu-id="a8eee-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-131">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a8eee-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="a8eee-133">Columns</span></span>  
  
|<span data-ttu-id="a8eee-134">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-134">ColumnName</span></span>|<span data-ttu-id="a8eee-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-136">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-137">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-137">String</span></span>|  
|<span data-ttu-id="a8eee-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-139">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-139">String</span></span>|  
|<span data-ttu-id="a8eee-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-140">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-141">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-141">String</span></span>|  
|<span data-ttu-id="a8eee-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-142">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-143">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-143">String</span></span>|  
|<span data-ttu-id="a8eee-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-144">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-145">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-145">Guid</span></span>|  
|<span data-ttu-id="a8eee-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-146">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-147">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-147">Int64</span></span>|  
|<span data-ttu-id="a8eee-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-149">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-149">Int64</span></span>|  
|<span data-ttu-id="a8eee-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="a8eee-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-151">Boolean</span></span>|  
|<span data-ttu-id="a8eee-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="a8eee-153">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-153">String</span></span>|  
|<span data-ttu-id="a8eee-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="a8eee-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="a8eee-155">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-155">Int64</span></span>|  
|<span data-ttu-id="a8eee-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-156">IS_NULLABLE</span></span>|<span data-ttu-id="a8eee-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-157">Boolean</span></span>|  
|<span data-ttu-id="a8eee-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-158">DATA_TYPE</span></span>|<span data-ttu-id="a8eee-159">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-159">Int32</span></span>|  
|<span data-ttu-id="a8eee-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-160">TYPE_GUID</span></span>|<span data-ttu-id="a8eee-161">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-161">Guid</span></span>|  
|<span data-ttu-id="a8eee-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a8eee-163">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-163">Int64</span></span>|  
|<span data-ttu-id="a8eee-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a8eee-165">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-165">Int64</span></span>|  
|<span data-ttu-id="a8eee-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a8eee-167">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-167">Int32</span></span>|  
|<span data-ttu-id="a8eee-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a8eee-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="a8eee-169">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-169">Int16</span></span>|  
|<span data-ttu-id="a8eee-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="a8eee-171">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-171">Int64</span></span>|  
|<span data-ttu-id="a8eee-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="a8eee-173">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-173">String</span></span>|  
|<span data-ttu-id="a8eee-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="a8eee-175">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-175">String</span></span>|  
|<span data-ttu-id="a8eee-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="a8eee-177">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-177">String</span></span>|  
|<span data-ttu-id="a8eee-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="a8eee-179">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-179">String</span></span>|  
|<span data-ttu-id="a8eee-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="a8eee-181">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-181">String</span></span>|  
|<span data-ttu-id="a8eee-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-182">COLLATION_NAME</span></span>|<span data-ttu-id="a8eee-183">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-183">String</span></span>|  
|<span data-ttu-id="a8eee-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="a8eee-185">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-185">String</span></span>|  
|<span data-ttu-id="a8eee-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="a8eee-187">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-187">String</span></span>|  
|<span data-ttu-id="a8eee-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-188">DOMAIN_NAME</span></span>|<span data-ttu-id="a8eee-189">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-189">String</span></span>|  
|<span data-ttu-id="a8eee-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-190">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-191">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-191">String</span></span>|  
|<span data-ttu-id="a8eee-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="a8eee-192">COLUMN_LCID</span></span>|<span data-ttu-id="a8eee-193">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-193">Int32</span></span>|  
|<span data-ttu-id="a8eee-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="a8eee-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="a8eee-195">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-195">Int32</span></span>|  
|<span data-ttu-id="a8eee-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="a8eee-196">COLUMN_SORTID</span></span>|<span data-ttu-id="a8eee-197">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-197">Int32</span></span>|  
|<span data-ttu-id="a8eee-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="a8eee-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="a8eee-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="a8eee-199">Byte[]</span></span>|  
|<span data-ttu-id="a8eee-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="a8eee-200">IS_COMPUTED</span></span>|<span data-ttu-id="a8eee-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a8eee-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8eee-202">Procedures</span></span>  
  
|<span data-ttu-id="a8eee-203">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-203">ColumnName</span></span>|<span data-ttu-id="a8eee-204">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a8eee-206">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-206">String</span></span>|  
|<span data-ttu-id="a8eee-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a8eee-208">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-208">String</span></span>|  
|<span data-ttu-id="a8eee-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="a8eee-210">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-210">String</span></span>|  
|<span data-ttu-id="a8eee-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="a8eee-212">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-212">Int16</span></span>|  
|<span data-ttu-id="a8eee-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="a8eee-214">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-214">String</span></span>|  
|<span data-ttu-id="a8eee-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-215">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-216">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-216">String</span></span>|  
|<span data-ttu-id="a8eee-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-217">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-218">DateTime</span></span>|  
|<span data-ttu-id="a8eee-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-219">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="a8eee-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a8eee-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="a8eee-222">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-222">ColumnName</span></span>|<span data-ttu-id="a8eee-223">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a8eee-225">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-225">String</span></span>|  
|<span data-ttu-id="a8eee-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a8eee-227">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-227">String</span></span>|  
|<span data-ttu-id="a8eee-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="a8eee-229">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-229">String</span></span>|  
|<span data-ttu-id="a8eee-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-230">PARAMETER_NAME</span></span>|<span data-ttu-id="a8eee-231">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-231">String</span></span>|  
|<span data-ttu-id="a8eee-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-233">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-233">Int32</span></span>|  
|<span data-ttu-id="a8eee-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="a8eee-235">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-235">Int32</span></span>|  
|<span data-ttu-id="a8eee-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="a8eee-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-237">Boolean</span></span>|  
|<span data-ttu-id="a8eee-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="a8eee-239">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-239">String</span></span>|  
|<span data-ttu-id="a8eee-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-240">IS_NULLABLE</span></span>|<span data-ttu-id="a8eee-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-241">Boolean</span></span>|  
|<span data-ttu-id="a8eee-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-242">DATA_TYPE</span></span>|<span data-ttu-id="a8eee-243">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-243">Int32</span></span>|  
|<span data-ttu-id="a8eee-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a8eee-245">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-245">Int64</span></span>|  
|<span data-ttu-id="a8eee-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a8eee-247">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-247">Int64</span></span>|  
|<span data-ttu-id="a8eee-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a8eee-249">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-249">Int32</span></span>|  
|<span data-ttu-id="a8eee-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a8eee-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="a8eee-251">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-251">Int16</span></span>|  
|<span data-ttu-id="a8eee-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-252">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-253">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-253">String</span></span>|  
|<span data-ttu-id="a8eee-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-254">TYPE_NAME</span></span>|<span data-ttu-id="a8eee-255">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-255">String</span></span>|  
|<span data-ttu-id="a8eee-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="a8eee-257">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="a8eee-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="a8eee-258">Catalog</span></span>  
  
|<span data-ttu-id="a8eee-259">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-259">ColumnName</span></span>|<span data-ttu-id="a8eee-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-261">CATALOG_NAME</span></span>|<span data-ttu-id="a8eee-262">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-262">String</span></span>|  
|<span data-ttu-id="a8eee-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-263">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-264">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a8eee-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="a8eee-265">Indexes</span></span>  
  
|<span data-ttu-id="a8eee-266">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-266">ColumnName</span></span>|<span data-ttu-id="a8eee-267">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-268">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-269">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-269">String</span></span>|  
|<span data-ttu-id="a8eee-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-271">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-271">String</span></span>|  
|<span data-ttu-id="a8eee-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-272">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-273">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-273">String</span></span>|  
|<span data-ttu-id="a8eee-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-274">INDEX_CATALOG</span></span>|<span data-ttu-id="a8eee-275">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-275">String</span></span>|  
|<span data-ttu-id="a8eee-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="a8eee-277">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-277">String</span></span>|  
|<span data-ttu-id="a8eee-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-278">INDEX_NAME</span></span>|<span data-ttu-id="a8eee-279">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-279">String</span></span>|  
|<span data-ttu-id="a8eee-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="a8eee-280">PRIMARY_KEY</span></span>|<span data-ttu-id="a8eee-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-281">Boolean</span></span>|  
|<span data-ttu-id="a8eee-282">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="a8eee-282">UNIQUE</span></span>|<span data-ttu-id="a8eee-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-283">Boolean</span></span>|  
|<span data-ttu-id="a8eee-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="a8eee-284">CLUSTERED</span></span>|<span data-ttu-id="a8eee-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-285">Boolean</span></span>|  
|<span data-ttu-id="a8eee-286">TYP</span><span class="sxs-lookup"><span data-stu-id="a8eee-286">TYPE</span></span>|<span data-ttu-id="a8eee-287">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-287">Int32</span></span>|  
|<span data-ttu-id="a8eee-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="a8eee-288">FILL_FACTOR</span></span>|<span data-ttu-id="a8eee-289">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-289">Int32</span></span>|  
|<span data-ttu-id="a8eee-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="a8eee-290">INITIAL_SIZE</span></span>|<span data-ttu-id="a8eee-291">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-291">Int32</span></span>|  
|<span data-ttu-id="a8eee-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="a8eee-292">NULLS</span></span>|<span data-ttu-id="a8eee-293">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-293">Int32</span></span>|  
|<span data-ttu-id="a8eee-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="a8eee-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="a8eee-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-295">Boolean</span></span>|  
|<span data-ttu-id="a8eee-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="a8eee-296">AUTO_UPDATE</span></span>|<span data-ttu-id="a8eee-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-297">Boolean</span></span>|  
|<span data-ttu-id="a8eee-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="a8eee-298">NULL_COLLATION</span></span>|<span data-ttu-id="a8eee-299">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-299">Int32</span></span>|  
|<span data-ttu-id="a8eee-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-301">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-301">Int64</span></span>|  
|<span data-ttu-id="a8eee-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-302">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-303">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-303">String</span></span>|  
|<span data-ttu-id="a8eee-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-304">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-305">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-305">Guid</span></span>|  
|<span data-ttu-id="a8eee-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-306">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-307">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-307">Int64</span></span>|  
|<span data-ttu-id="a8eee-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="a8eee-308">COLLATION</span></span>|<span data-ttu-id="a8eee-309">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-309">Int16</span></span>|  
|<span data-ttu-id="a8eee-310">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="a8eee-310">CARDINALITY</span></span>|<span data-ttu-id="a8eee-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="a8eee-311">Decimal</span></span>|  
|<span data-ttu-id="a8eee-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="a8eee-312">PAGES</span></span>|<span data-ttu-id="a8eee-313">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-313">Int32</span></span>|  
|<span data-ttu-id="a8eee-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-314">FILTER_CONDITION</span></span>|<span data-ttu-id="a8eee-315">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-315">String</span></span>|  
|<span data-ttu-id="a8eee-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="a8eee-316">INTEGRATED</span></span>|<span data-ttu-id="a8eee-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="a8eee-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="a8eee-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="a8eee-319">Oracle OLE DB ovladače Microsoft podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="a8eee-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="a8eee-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="a8eee-320">Tables</span></span>  
  
-   <span data-ttu-id="a8eee-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="a8eee-321">Columns</span></span>  
  
-   <span data-ttu-id="a8eee-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8eee-322">Procedures</span></span>  
  
-   <span data-ttu-id="a8eee-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="a8eee-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="a8eee-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a8eee-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="a8eee-325">zobrazení</span><span class="sxs-lookup"><span data-stu-id="a8eee-325">Views</span></span>  
  
-   <span data-ttu-id="a8eee-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="a8eee-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="a8eee-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="a8eee-327">Tables</span></span>  
  
|<span data-ttu-id="a8eee-328">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-328">ColumnName</span></span>|<span data-ttu-id="a8eee-329">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-330">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-331">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-331">String</span></span>|  
|<span data-ttu-id="a8eee-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-333">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-333">String</span></span>|  
|<span data-ttu-id="a8eee-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-334">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-335">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-335">String</span></span>|  
|<span data-ttu-id="a8eee-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-336">TABLE_TYPE</span></span>|<span data-ttu-id="a8eee-337">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-337">String</span></span>|  
|<span data-ttu-id="a8eee-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-338">TABLE_GUID</span></span>|<span data-ttu-id="a8eee-339">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-339">Guid</span></span>|  
|<span data-ttu-id="a8eee-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-340">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-341">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-341">String</span></span>|  
|<span data-ttu-id="a8eee-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-342">TABLE_PROPID</span></span>|<span data-ttu-id="a8eee-343">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-343">Int64</span></span>|  
|<span data-ttu-id="a8eee-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-344">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-345">DateTime</span></span>|  
|<span data-ttu-id="a8eee-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-346">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a8eee-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="a8eee-348">Columns</span></span>  
  
|<span data-ttu-id="a8eee-349">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-349">ColumnName</span></span>|<span data-ttu-id="a8eee-350">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-351">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-352">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-352">String</span></span>|  
|<span data-ttu-id="a8eee-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-354">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-354">String</span></span>|  
|<span data-ttu-id="a8eee-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-355">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-356">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-356">String</span></span>|  
|<span data-ttu-id="a8eee-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-357">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-358">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-358">String</span></span>|  
|<span data-ttu-id="a8eee-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-359">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-360">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-360">Guid</span></span>|  
|<span data-ttu-id="a8eee-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-361">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-362">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-362">Int64</span></span>|  
|<span data-ttu-id="a8eee-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-364">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-364">Int64</span></span>|  
|<span data-ttu-id="a8eee-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="a8eee-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-366">Boolean</span></span>|  
|<span data-ttu-id="a8eee-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="a8eee-368">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-368">String</span></span>|  
|<span data-ttu-id="a8eee-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="a8eee-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="a8eee-370">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-370">Int64</span></span>|  
|<span data-ttu-id="a8eee-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-371">IS_NULLABLE</span></span>|<span data-ttu-id="a8eee-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-372">Boolean</span></span>|  
|<span data-ttu-id="a8eee-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-373">DATA_TYPE</span></span>|<span data-ttu-id="a8eee-374">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-374">Int32</span></span>|  
|<span data-ttu-id="a8eee-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-375">TYPE_GUID</span></span>|<span data-ttu-id="a8eee-376">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-376">Guid</span></span>|  
|<span data-ttu-id="a8eee-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a8eee-378">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-378">Int64</span></span>|  
|<span data-ttu-id="a8eee-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a8eee-380">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-380">Int64</span></span>|  
|<span data-ttu-id="a8eee-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a8eee-382">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-382">Int32</span></span>|  
|<span data-ttu-id="a8eee-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a8eee-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="a8eee-384">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-384">Int16</span></span>|  
|<span data-ttu-id="a8eee-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="a8eee-386">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-386">Int64</span></span>|  
|<span data-ttu-id="a8eee-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="a8eee-388">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-388">String</span></span>|  
|<span data-ttu-id="a8eee-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="a8eee-390">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-390">String</span></span>|  
|<span data-ttu-id="a8eee-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="a8eee-392">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-392">String</span></span>|  
|<span data-ttu-id="a8eee-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="a8eee-394">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-394">String</span></span>|  
|<span data-ttu-id="a8eee-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="a8eee-396">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-396">String</span></span>|  
|<span data-ttu-id="a8eee-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-397">COLLATION_NAME</span></span>|<span data-ttu-id="a8eee-398">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-398">String</span></span>|  
|<span data-ttu-id="a8eee-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="a8eee-400">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-400">String</span></span>|  
|<span data-ttu-id="a8eee-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="a8eee-402">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-402">String</span></span>|  
|<span data-ttu-id="a8eee-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-403">DOMAIN_NAME</span></span>|<span data-ttu-id="a8eee-404">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-404">String</span></span>|  
|<span data-ttu-id="a8eee-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-405">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-406">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a8eee-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8eee-407">Procedures</span></span>  
  
|<span data-ttu-id="a8eee-408">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-408">ColumnName</span></span>|<span data-ttu-id="a8eee-409">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a8eee-411">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-411">String</span></span>|  
|<span data-ttu-id="a8eee-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a8eee-413">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-413">String</span></span>|  
|<span data-ttu-id="a8eee-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="a8eee-415">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-415">String</span></span>|  
|<span data-ttu-id="a8eee-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="a8eee-417">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-417">Int16</span></span>|  
|<span data-ttu-id="a8eee-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="a8eee-419">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-419">String</span></span>|  
|<span data-ttu-id="a8eee-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-420">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-421">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-421">String</span></span>|  
|<span data-ttu-id="a8eee-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-422">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-423">DateTime</span></span>|  
|<span data-ttu-id="a8eee-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-424">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="a8eee-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="a8eee-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="a8eee-427">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-427">ColumnName</span></span>|<span data-ttu-id="a8eee-428">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a8eee-430">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-430">String</span></span>|  
|<span data-ttu-id="a8eee-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a8eee-432">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-432">String</span></span>|  
|<span data-ttu-id="a8eee-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="a8eee-434">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-434">String</span></span>|  
|<span data-ttu-id="a8eee-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-435">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-436">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-436">String</span></span>|  
|<span data-ttu-id="a8eee-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-437">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-438">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-438">Guid</span></span>|  
|<span data-ttu-id="a8eee-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-439">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-440">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-440">Int64</span></span>|  
|<span data-ttu-id="a8eee-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="a8eee-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="a8eee-442">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-442">Int64</span></span>|  
|<span data-ttu-id="a8eee-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-444">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-444">Int64</span></span>|  
|<span data-ttu-id="a8eee-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-445">IS_NULLABLE</span></span>|<span data-ttu-id="a8eee-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-446">Boolean</span></span>|  
|<span data-ttu-id="a8eee-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-447">DATA_TYPE</span></span>|<span data-ttu-id="a8eee-448">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-448">Int32</span></span>|  
|<span data-ttu-id="a8eee-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-449">TYPE_GUID</span></span>|<span data-ttu-id="a8eee-450">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-450">Guid</span></span>|  
|<span data-ttu-id="a8eee-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a8eee-452">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-452">Int64</span></span>|  
|<span data-ttu-id="a8eee-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a8eee-454">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-454">Int64</span></span>|  
|<span data-ttu-id="a8eee-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a8eee-456">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-456">Int32</span></span>|  
|<span data-ttu-id="a8eee-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a8eee-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="a8eee-458">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-458">Int16</span></span>|  
|<span data-ttu-id="a8eee-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-459">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-460">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-460">String</span></span>|  
|<span data-ttu-id="a8eee-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="a8eee-461">OVERLOAD</span></span>|<span data-ttu-id="a8eee-462">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a8eee-463">zobrazení</span><span class="sxs-lookup"><span data-stu-id="a8eee-463">Views</span></span>  
  
|<span data-ttu-id="a8eee-464">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-464">ColumnName</span></span>|<span data-ttu-id="a8eee-465">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-466">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-467">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-467">String</span></span>|  
|<span data-ttu-id="a8eee-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-469">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-469">String</span></span>|  
|<span data-ttu-id="a8eee-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-470">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-471">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-471">String</span></span>|  
|<span data-ttu-id="a8eee-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="a8eee-473">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-473">String</span></span>|  
|<span data-ttu-id="a8eee-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="a8eee-474">CHECK_OPTION</span></span>|<span data-ttu-id="a8eee-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-475">Boolean</span></span>|  
|<span data-ttu-id="a8eee-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-476">IS_UPDATABLE</span></span>|<span data-ttu-id="a8eee-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-477">Boolean</span></span>|  
|<span data-ttu-id="a8eee-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-478">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-479">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-479">String</span></span>|  
|<span data-ttu-id="a8eee-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-480">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-481">DateTime</span></span>|  
|<span data-ttu-id="a8eee-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-482">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a8eee-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="a8eee-484">Indexes</span></span>  
  
|<span data-ttu-id="a8eee-485">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-485">ColumnName</span></span>|<span data-ttu-id="a8eee-486">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-487">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-488">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-488">String</span></span>|  
|<span data-ttu-id="a8eee-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-490">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-490">String</span></span>|  
|<span data-ttu-id="a8eee-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-491">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-492">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-492">String</span></span>|  
|<span data-ttu-id="a8eee-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-493">INDEX_CATALOG</span></span>|<span data-ttu-id="a8eee-494">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-494">String</span></span>|  
|<span data-ttu-id="a8eee-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="a8eee-496">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-496">String</span></span>|  
|<span data-ttu-id="a8eee-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-497">INDEX_NAME</span></span>|<span data-ttu-id="a8eee-498">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-498">String</span></span>|  
|<span data-ttu-id="a8eee-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="a8eee-499">PRIMARY_KEY</span></span>|<span data-ttu-id="a8eee-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-500">Boolean</span></span>|  
|<span data-ttu-id="a8eee-501">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="a8eee-501">UNIQUE</span></span>|<span data-ttu-id="a8eee-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-502">Boolean</span></span>|  
|<span data-ttu-id="a8eee-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="a8eee-503">CLUSTERED</span></span>|<span data-ttu-id="a8eee-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-504">Boolean</span></span>|  
|<span data-ttu-id="a8eee-505">TYP</span><span class="sxs-lookup"><span data-stu-id="a8eee-505">TYPE</span></span>|<span data-ttu-id="a8eee-506">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-506">Int32</span></span>|  
|<span data-ttu-id="a8eee-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="a8eee-507">FILL_FACTOR</span></span>|<span data-ttu-id="a8eee-508">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-508">Int32</span></span>|  
|<span data-ttu-id="a8eee-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="a8eee-509">INITIAL_SIZE</span></span>|<span data-ttu-id="a8eee-510">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-510">Int32</span></span>|  
|<span data-ttu-id="a8eee-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="a8eee-511">NULLS</span></span>|<span data-ttu-id="a8eee-512">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-512">Int32</span></span>|  
|<span data-ttu-id="a8eee-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="a8eee-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="a8eee-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-514">Boolean</span></span>|  
|<span data-ttu-id="a8eee-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="a8eee-515">AUTO_UPDATE</span></span>|<span data-ttu-id="a8eee-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-516">Boolean</span></span>|  
|<span data-ttu-id="a8eee-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="a8eee-517">NULL_COLLATION</span></span>|<span data-ttu-id="a8eee-518">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-518">Int32</span></span>|  
|<span data-ttu-id="a8eee-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-520">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-520">Int64</span></span>|  
|<span data-ttu-id="a8eee-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-521">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-522">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-522">String</span></span>|  
|<span data-ttu-id="a8eee-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-523">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-524">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-524">Guid</span></span>|  
|<span data-ttu-id="a8eee-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-525">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-526">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-526">Int64</span></span>|  
|<span data-ttu-id="a8eee-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="a8eee-527">COLLATION</span></span>|<span data-ttu-id="a8eee-528">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-528">Int16</span></span>|  
|<span data-ttu-id="a8eee-529">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="a8eee-529">CARDINALITY</span></span>|<span data-ttu-id="a8eee-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="a8eee-530">Decimal</span></span>|  
|<span data-ttu-id="a8eee-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="a8eee-531">PAGES</span></span>|<span data-ttu-id="a8eee-532">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-532">Int32</span></span>|  
|<span data-ttu-id="a8eee-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-533">FILTER_CONDITION</span></span>|<span data-ttu-id="a8eee-534">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-534">String</span></span>|  
|<span data-ttu-id="a8eee-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="a8eee-535">INTEGRATED</span></span>|<span data-ttu-id="a8eee-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="a8eee-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="a8eee-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="a8eee-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="a8eee-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="a8eee-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="a8eee-539">Tables</span></span>  
  
-   <span data-ttu-id="a8eee-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="a8eee-540">Columns</span></span>  
  
-   <span data-ttu-id="a8eee-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8eee-541">Procedures</span></span>  
  
-   <span data-ttu-id="a8eee-542">zobrazení</span><span class="sxs-lookup"><span data-stu-id="a8eee-542">Views</span></span>  
  
-   <span data-ttu-id="a8eee-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="a8eee-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="a8eee-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="a8eee-544">Tables</span></span>  
  
|<span data-ttu-id="a8eee-545">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-545">ColumnName</span></span>|<span data-ttu-id="a8eee-546">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-547">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-548">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-548">String</span></span>|  
|<span data-ttu-id="a8eee-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-550">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-550">String</span></span>|  
|<span data-ttu-id="a8eee-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-551">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-552">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-552">String</span></span>|  
|<span data-ttu-id="a8eee-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-553">TABLE_TYPE</span></span>|<span data-ttu-id="a8eee-554">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-554">String</span></span>|  
|<span data-ttu-id="a8eee-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-555">TABLE_GUID</span></span>|<span data-ttu-id="a8eee-556">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-556">Guid</span></span>|  
|<span data-ttu-id="a8eee-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-557">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-558">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-558">String</span></span>|  
|<span data-ttu-id="a8eee-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-559">TABLE_PROPID</span></span>|<span data-ttu-id="a8eee-560">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-560">Int64</span></span>|  
|<span data-ttu-id="a8eee-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-561">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-562">DateTime</span></span>|  
|<span data-ttu-id="a8eee-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-563">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a8eee-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="a8eee-565">Columns</span></span>  
  
|<span data-ttu-id="a8eee-566">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-566">ColumnName</span></span>|<span data-ttu-id="a8eee-567">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-568">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-569">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-569">String</span></span>|  
|<span data-ttu-id="a8eee-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-571">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-571">String</span></span>|  
|<span data-ttu-id="a8eee-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-572">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-573">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-573">String</span></span>|  
|<span data-ttu-id="a8eee-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-574">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-575">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-575">String</span></span>|  
|<span data-ttu-id="a8eee-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-576">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-577">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-577">Guid</span></span>|  
|<span data-ttu-id="a8eee-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-578">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-579">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-579">Int64</span></span>|  
|<span data-ttu-id="a8eee-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-581">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-581">Int64</span></span>|  
|<span data-ttu-id="a8eee-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="a8eee-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-583">Boolean</span></span>|  
|<span data-ttu-id="a8eee-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="a8eee-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="a8eee-585">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-585">String</span></span>|  
|<span data-ttu-id="a8eee-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="a8eee-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="a8eee-587">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-587">Int64</span></span>|  
|<span data-ttu-id="a8eee-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-588">IS_NULLABLE</span></span>|<span data-ttu-id="a8eee-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-589">Boolean</span></span>|  
|<span data-ttu-id="a8eee-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-590">DATA_TYPE</span></span>|<span data-ttu-id="a8eee-591">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-591">Int32</span></span>|  
|<span data-ttu-id="a8eee-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-592">TYPE_GUID</span></span>|<span data-ttu-id="a8eee-593">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-593">Guid</span></span>|  
|<span data-ttu-id="a8eee-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="a8eee-595">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-595">Int64</span></span>|  
|<span data-ttu-id="a8eee-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a8eee-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="a8eee-597">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-597">Int64</span></span>|  
|<span data-ttu-id="a8eee-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="a8eee-599">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-599">Int32</span></span>|  
|<span data-ttu-id="a8eee-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="a8eee-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="a8eee-601">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-601">Int16</span></span>|  
|<span data-ttu-id="a8eee-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="a8eee-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="a8eee-603">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-603">Int64</span></span>|  
|<span data-ttu-id="a8eee-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="a8eee-605">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-605">String</span></span>|  
|<span data-ttu-id="a8eee-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="a8eee-607">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-607">String</span></span>|  
|<span data-ttu-id="a8eee-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="a8eee-609">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-609">String</span></span>|  
|<span data-ttu-id="a8eee-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="a8eee-611">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-611">String</span></span>|  
|<span data-ttu-id="a8eee-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="a8eee-613">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-613">String</span></span>|  
|<span data-ttu-id="a8eee-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-614">COLLATION_NAME</span></span>|<span data-ttu-id="a8eee-615">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-615">String</span></span>|  
|<span data-ttu-id="a8eee-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="a8eee-617">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-617">String</span></span>|  
|<span data-ttu-id="a8eee-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="a8eee-619">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-619">String</span></span>|  
|<span data-ttu-id="a8eee-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-620">DOMAIN_NAME</span></span>|<span data-ttu-id="a8eee-621">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-621">String</span></span>|  
|<span data-ttu-id="a8eee-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-622">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-623">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a8eee-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8eee-624">Procedures</span></span>  
  
|<span data-ttu-id="a8eee-625">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-625">ColumnName</span></span>|<span data-ttu-id="a8eee-626">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="a8eee-628">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-628">String</span></span>|  
|<span data-ttu-id="a8eee-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="a8eee-630">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-630">String</span></span>|  
|<span data-ttu-id="a8eee-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="a8eee-632">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-632">String</span></span>|  
|<span data-ttu-id="a8eee-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8eee-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="a8eee-634">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-634">Int16</span></span>|  
|<span data-ttu-id="a8eee-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="a8eee-636">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-636">String</span></span>|  
|<span data-ttu-id="a8eee-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-637">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-638">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-638">String</span></span>|  
|<span data-ttu-id="a8eee-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-639">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-640">DateTime</span></span>|  
|<span data-ttu-id="a8eee-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-641">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a8eee-643">zobrazení</span><span class="sxs-lookup"><span data-stu-id="a8eee-643">Views</span></span>  
  
|<span data-ttu-id="a8eee-644">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-644">ColumnName</span></span>|<span data-ttu-id="a8eee-645">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-646">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-647">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-647">String</span></span>|  
|<span data-ttu-id="a8eee-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-649">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-649">String</span></span>|  
|<span data-ttu-id="a8eee-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-650">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-651">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-651">String</span></span>|  
|<span data-ttu-id="a8eee-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="a8eee-653">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-653">String</span></span>|  
|<span data-ttu-id="a8eee-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="a8eee-654">CHECK_OPTION</span></span>|<span data-ttu-id="a8eee-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-655">Boolean</span></span>|  
|<span data-ttu-id="a8eee-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="a8eee-656">IS_UPDATABLE</span></span>|<span data-ttu-id="a8eee-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-657">Boolean</span></span>|  
|<span data-ttu-id="a8eee-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="a8eee-658">DESCRIPTION</span></span>|<span data-ttu-id="a8eee-659">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-659">String</span></span>|  
|<span data-ttu-id="a8eee-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a8eee-660">DATE_CREATED</span></span>|<span data-ttu-id="a8eee-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-661">DateTime</span></span>|  
|<span data-ttu-id="a8eee-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="a8eee-662">DATE_MODIFIED</span></span>|<span data-ttu-id="a8eee-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="a8eee-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a8eee-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="a8eee-664">Indexes</span></span>  
  
|<span data-ttu-id="a8eee-665">columnName</span><span class="sxs-lookup"><span data-stu-id="a8eee-665">ColumnName</span></span>|<span data-ttu-id="a8eee-666">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a8eee-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="a8eee-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-667">TABLE_CATALOG</span></span>|<span data-ttu-id="a8eee-668">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-668">String</span></span>|  
|<span data-ttu-id="a8eee-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="a8eee-670">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-670">String</span></span>|  
|<span data-ttu-id="a8eee-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-671">TABLE_NAME</span></span>|<span data-ttu-id="a8eee-672">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-672">String</span></span>|  
|<span data-ttu-id="a8eee-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8eee-673">INDEX_CATALOG</span></span>|<span data-ttu-id="a8eee-674">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-674">String</span></span>|  
|<span data-ttu-id="a8eee-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a8eee-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="a8eee-676">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-676">String</span></span>|  
|<span data-ttu-id="a8eee-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-677">INDEX_NAME</span></span>|<span data-ttu-id="a8eee-678">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-678">String</span></span>|  
|<span data-ttu-id="a8eee-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="a8eee-679">PRIMARY_KEY</span></span>|<span data-ttu-id="a8eee-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-680">Boolean</span></span>|  
|<span data-ttu-id="a8eee-681">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="a8eee-681">UNIQUE</span></span>|<span data-ttu-id="a8eee-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-682">Boolean</span></span>|  
|<span data-ttu-id="a8eee-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="a8eee-683">CLUSTERED</span></span>|<span data-ttu-id="a8eee-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-684">Boolean</span></span>|  
|<span data-ttu-id="a8eee-685">TYP</span><span class="sxs-lookup"><span data-stu-id="a8eee-685">TYPE</span></span>|<span data-ttu-id="a8eee-686">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-686">Int32</span></span>|  
|<span data-ttu-id="a8eee-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="a8eee-687">FILL_FACTOR</span></span>|<span data-ttu-id="a8eee-688">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-688">Int32</span></span>|  
|<span data-ttu-id="a8eee-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="a8eee-689">INITIAL_SIZE</span></span>|<span data-ttu-id="a8eee-690">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-690">Int32</span></span>|  
|<span data-ttu-id="a8eee-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="a8eee-691">NULLS</span></span>|<span data-ttu-id="a8eee-692">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-692">Int32</span></span>|  
|<span data-ttu-id="a8eee-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="a8eee-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="a8eee-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-694">Boolean</span></span>|  
|<span data-ttu-id="a8eee-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="a8eee-695">AUTO_UPDATE</span></span>|<span data-ttu-id="a8eee-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-696">Boolean</span></span>|  
|<span data-ttu-id="a8eee-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="a8eee-697">NULL_COLLATION</span></span>|<span data-ttu-id="a8eee-698">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-698">Int32</span></span>|  
|<span data-ttu-id="a8eee-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="a8eee-700">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-700">Int64</span></span>|  
|<span data-ttu-id="a8eee-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a8eee-701">COLUMN_NAME</span></span>|<span data-ttu-id="a8eee-702">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-702">String</span></span>|  
|<span data-ttu-id="a8eee-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-703">COLUMN_GUID</span></span>|<span data-ttu-id="a8eee-704">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="a8eee-704">Guid</span></span>|  
|<span data-ttu-id="a8eee-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="a8eee-705">COLUMN_PROPID</span></span>|<span data-ttu-id="a8eee-706">Int64</span><span class="sxs-lookup"><span data-stu-id="a8eee-706">Int64</span></span>|  
|<span data-ttu-id="a8eee-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="a8eee-707">COLLATION</span></span>|<span data-ttu-id="a8eee-708">Int16</span><span class="sxs-lookup"><span data-stu-id="a8eee-708">Int16</span></span>|  
|<span data-ttu-id="a8eee-709">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="a8eee-709">CARDINALITY</span></span>|<span data-ttu-id="a8eee-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="a8eee-710">Decimal</span></span>|  
|<span data-ttu-id="a8eee-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="a8eee-711">PAGES</span></span>|<span data-ttu-id="a8eee-712">Int32</span><span class="sxs-lookup"><span data-stu-id="a8eee-712">Int32</span></span>|  
|<span data-ttu-id="a8eee-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="a8eee-713">FILTER_CONDITION</span></span>|<span data-ttu-id="a8eee-714">String</span><span class="sxs-lookup"><span data-stu-id="a8eee-714">String</span></span>|  
|<span data-ttu-id="a8eee-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="a8eee-715">INTEGRATED</span></span>|<span data-ttu-id="a8eee-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8eee-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8eee-717">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8eee-717">See Also</span></span>  
 [<span data-ttu-id="a8eee-718">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="a8eee-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
