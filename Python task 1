# Map-assignment
##generate_car_matrix
    def generate_car_matrix(df: pd.DataFrame) -> pd.DataFrame:
    """
    Creates a DataFrame for id combinations.

    Args:
        df (pandas.DataFrame)

    Returns:
        pandas.DataFrame: Matrix generated with 'car' values, 
                          where 'id_1' and 'id_2' are used as indices and columns respectively.
    """
    car_matrix = df.pivot(index='id_1', columns='id_2', values='car')
    return car_matrix
##get_type_count
def get_type_count(df: pd.DataFrame) -> dict:
    """
    Categorizes 'car' values into types and returns a dictionary of counts.

    Args:
        df (pandas.DataFrame)

    Returns:
        dict: A dictionary with car types as keys and their counts as values.
    """
    type_counts = df['car'].value_counts().to_dict()
    return type_counts
##get_bus_indexes
def get_bus_indexes(df: pd.DataFrame) -> list:
    """
    Returns the indexes where the 'bus' values are greater than twice the mean.

    Args:
        df (pandas.DataFrame)

    Returns:
        list: List of indexes where 'bus' values exceed twice the mean.
    """
    bus_indexes = df[df['car'] == 'bus'].index[df['car'] == 'bus'].tolist()
    mean_bus_value = df.loc[bus_indexes, 'car'].mean()
    selected_indexes = [index for index in bus_indexes if df.loc[index, 'car'] > 2 * mean_bus_value]
    return selected_indexes
##filter_routes
def filter_routes(df: pd.DataFrame) -> list:
    """
    Filters and returns routes with average 'truck' values greater than 7.

    Args:
        df (pandas.DataFrame)

    Returns:
        list: List of route names with average 'truck' values greater than 7.
    """
    average_truck_values = df.groupby('route')['car'].mean()
    selected_routes = average_truck_values[average_truck_values > 7].index.tolist()
    return selected_routes
##multiply_matrix
def multiply_matrix(matrix: pd.DataFrame) -> pd.DataFrame:
    """
    Multiplies matrix values with custom conditions.

    Args:
        matrix (pandas.DataFrame)

    Returns:
        pandas.DataFrame: Modified matrix with values multiplied based on custom conditions.
    """
    # Example: Multiply values greater than 10 by 2
    modified_matrix = matrix.applymap(lambda x: x * 2 if x > 10 else x)
    return modified_matrix
##time_check
def time_check(df: pd.DataFrame) -> pd.Series:
    """
    Use shared dataset-2 to verify the completeness of the data by checking whether the timestamps for each unique (`id`, `id_2`) pair cover a full 24-hour and 7 days period

    Args:
        df (pandas.DataFrame)

    Returns:
        pd.Series: return a boolean series
    """
    completeness_check = df.groupby(['id', 'id_2'])['timestamp'].agg(lambda x: (x.max() - x.min()).total_seconds() >= 24*60*60*7)
    return completeness_check


  
